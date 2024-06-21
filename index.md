<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Embed Markdown</title>
    <script src="https://cdn.jsdelivr.net/npm/showdown/dist/showdown.min.js"></script>
  </head>
  <body>
    <div id="content"></div>

    <script>
      document.addEventListener("DOMContentLoaded", function () {
        fetch("README.md")
          .then((response) => response.text())
          .then((markdown) => {
            console.log(markdown);
            var converter = new showdown.Converter();
            var html = converter.makeHtml(markdown);
            document.getElementById("content").innerHTML = html;
          })
          .catch((error) => {
            console.error("Error fetching or converting Markdown:", error);
          });
      });
    </script>
  </body>
</html>

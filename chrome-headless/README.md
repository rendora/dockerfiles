
# Headless Chrome

This is headless Chrome based on `justinribeiro/chrome-headless` dockerfile but modified to suit [Rendora](https://github.com/rendora/rendora)'s goal for server-side rendering, running this image is equivalent to running Chrome with the following flags

```bash
google-chrome --headless --no-sandbox --disable-setuid-sandbox \
                --disable-dev-shm-usage --disable-gpu --remote-debugging-address=0.0.0.0 \
                --remote-debugging-port=9222 --disable-remote-fonts --user-data-dir=/tmp
```

As you see, sandboxing is currently disabled; therefore it might not be your best choice to run this image with the default flags unless you trust the websites you navigate using it.


## How to use


``` bash
docker run --tmpfs /tmp --net=host rendora/chrome-headless
```

*note:* the `tmpfs` flag is optional but it's recommended for performance reasons since `rendora/chrome-headless` runs with flag `--user-data-dir=/tmp`
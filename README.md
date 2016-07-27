# Netbeans IDE inside Docker

This is my initial attempt in getting Netbeans IDE 8.1 running within a docker container.

## To use:

docker run -it --rm \
   -e DISPLAY \
   --net=host \
   -v /tmp/.X11-unix:/tmp/.X11-unix \
   -v $HOME/.Xauthority:/home/user/.Xauthority \
   area51/netbeans

You can also mount /home/user as an additional mount if you want to persist settings between sessions. With the IDE this is the best thing to do so you can persist both projects and IDE updates.

Also, you can also run it in the background by replacing -it --rm with -d if you so wish.

## Running on OSX

I've only tested this with running the image on a remote Linux server but presuming you have X11 installed on the mac:

 ssh -Y user@linux.box

Then run the docker command above.

Note: The only issues so far on OSX are:
* if you run on multiple screens, the IDE opens across all of them but the ide appears on just one of them.
* If you maximise the window the menus don't work correctly.


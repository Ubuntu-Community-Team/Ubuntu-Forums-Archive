---
title: "Alternatives to 'killall' command"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-03-06
I am required to shut down BEEP-MEDIA-PLAYER and KAFFEINE thru CLI
I use:
```
killall beep-media-player
```
or
```
killall kaffeine
```
But when using that command, the playlists aren't saved. Is there a way to shut down BMP or KAFFEINE thru CLI and still have the PLAYLIST preserved?

---

### Post by frodon on 2006-03-06
Maybe a kill -15 command will save the context before killing the process.
Use this command to find the process number : ```
ps-aef | grep -i beep-media-player
```and this command to kill the process : ```
kill -15 process_number
```

---

### Post by mority on 2006-03-06
With the kill and killall commands you are actually sending so called signals to processes. Possibly there is a signal to tell a process to save its data and then shut down. But can't tell you what this signal would be. In "man 1 kill" is a complete list of the system signals.

---

### Post by mority on 2006-03-06
kill -15 is the TERM signal which is default.

But maybe kill -3 would do it. The signal is called QUIT but I don't know what it does exactly.

---

### Post by frodon on 2006-03-06
Exact, kill -15 is the default and will not save the context (a google search confirm it), kill -1 seems to be the best way to get the context saved since it's the smoothest level, (maybe -3 is enought mority ;) )

---

### Post by ashrack on 2006-03-07
my results:
```
kill -1
```
will treminate the BMP instantly.
```
kill -3
```
will terminate BMP with a 3sec delay. First it will stop the sound and then it will quit it.

BUt none of them saves playlists.

---

### Post by ashrack on 2006-03-08
so theres no way to shut down BMP from CLI and still have BMP save its playlist upon exit??

---

### Post by mority on 2006-03-10
[QUOTE=ashrack]so theres no way to shut down BMP from CLI and still have BMP save its playlist upon exit??[/QUOTE]

Hey, it's open source, there is always a way :p 

Generally applications in a unix like OS are controllable through shell commands and the GUIs do not much more than calling the appropiate shell commands if the user pushes a certain button (this is a simplification of course). So you could just try to enter the name of the binary used to start the programm and append '--help' or '-h' to it and see if it gives you some info. You could also try and see if there is a man page for the command. Maybe the developers implemented exactly the feature you are asking for and you just don't know it because you always started the program through a GUI so far. If not, the only way I would see is to hack the code youself or convince someone to do it for you ;)

---


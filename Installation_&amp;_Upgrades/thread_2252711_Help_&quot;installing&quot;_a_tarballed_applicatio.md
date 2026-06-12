---
title: "Help &quot;installing&quot; a tarballed application for all users"
date: 2014-11-13
forum: Installation &amp; Upgrades
---

### Post by redvenomweb on 2014-11-13
I previously posted this question to the Gaming subforum but I think it might be more appropriate here.

I have an old free (as in lunch) game that I would like to install in Ubuntu 14.04 for all users; it was distributed as a tarball. I currently have the game in a subdirectory under /usr/games. The problem is that this game needs to have a working directory set in order to run properly (game assets, config file, high scores file). I have an old launcher that I made for 10.04 that uses **gnome-terminal** with the **--working-directory** and **-e** options to resolve this issue, like so:

** gnome-terminal --working-directory /usr/games/foogame -e /usr/games/foogame/foostart**

However, while the game can access the necessary assets, it cannot modify the config file or high score table. What permissions should I set on these files in order to allow modification? Should I set permissions on just those two specific files, or on the entire game folder?

Additionally, in order to run this game with sound in 14.04, I need to install the **alsa-oss** package and run the game this way (from the foogame directory):

** alsa-oss ./foostart**

What's the best way to integrate this with the working directory requirement?

---

### Post by Impavidus on 2014-11-14
Can't you use command line options or environment variables to change the working directory of that game to somewhere else than the current directory? Something like```
foostart --dir=/usr/games/foogame/
```
The proper way of allowing the game to update its high score list, but not allowing ordinary users to cheet and add their own changes manually into the high score list, is by using the set group ID (sgid) bit. Set the group of the game to something suitable. The games group usually exist already and is meant for those things. You can also set up a new group for this game only. Also change the group of the game's working directory and its contents to this group. Give the group write access to the game's working directory and its contents and set the sgid bit on the game.```
#First line is redundant if the executable is in the game's working directory
sudo chgrp games /usr/games/foogame/foostart
sudo chgrp -R games /usr/games/foogame/
#Probably OK already, but running this command won't do any harm
sudo chmod -R g+wX /usr/games/foogame/
sudo chmod g+s /usr/games/foogame/foostart
```

I think best practice would be installing the executable in /usr/local/bin/ and storing the other files in /usr/local/share/foogame/, but I don't know whether your game has the flexibility for that. Putting everything together in /usr/games/foogame will work too. User editable config files would normally be placed in the user's home directory.

I don't know about alsa-oss.

---

### Post by redvenomweb on 2014-11-14
The game doesn't support command line variables and I'm not at all concerned about users hacking the high score table.

If I **chgrp** the game directory to the **games** group, how does the OS know to grant proper read/write permissions to the config/score files when a normal user runs the game?  Do I have to manually add every user to that group, too?  Sorry, I'm not as familiar with the way group permissions work in Ubuntu.

Lastly, I'm thinking about solving the alsa-oss problem with a script.  Basically, create a new script (**fooscript**) that contains:

```

#!/bin/sh

alsa-oss ./foostart
```

...and then modify my **gnome-terminal** launcher listed above like so:

**gnome-terminal --working-directory /usr/games/foogame -e /usr/games/foogame/[COLOR=#0000ff]fooscript[/COLOR]**

Are there any special changes I'd have to do to get that to work with the group-based approach?

---

### Post by Impavidus on 2014-11-14
If you set the sgid bit on the executable, the game will always run belonging to the games group, even when the user running the game does not belong to that group. Note that the sgid bit only works on binary executables, not on shell scripts. If startfoo is a shell script starting the binary executable, you have to set the sgid bit on the binary.

If you don't care if the users make random changes to the game's directory (even accidentally), you can give everyone full write access to the files that may have to be modified and not worry about groups. Best to keep a backup in another directory, just in case someone breaks the game by corrupting the config file.

---

### Post by redvenomweb on 2014-11-14
Sounds like the best thing for me to do is create the above mentioned script, make a read-only copy of the config/score files (in the same folder with a .backup extension), and then just give r/w access to everyone (chmod 777) for the config/score files.

I'll give it a try.  Thanks a lot for your help!

---


---
title: "game sound toggling in feisty? (gweled &amp; frozen-bubble 2)"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by teddmeister2 on 2007-05-03
{both problems solved/worked around, see below for details} Original post: So far, in at least two games in feisty I haven't been able to find *any* way to toggle the sound in the games frozen bubble and gweled (while I'm pretty sure I was able to in edgy).  This makes it impossible to multi-task in ways such as: playing songs or lectures or podcasts while playing, or watching a video while playing the game and surfing the net at the same time (I guess I might have a.d.d.).  But anyway, have all possibilities for disabling sound in these games been removed in the feisty versions?  Is there a setting in the gui that i missed?  Is there an option I can pass to each game in the command line that will disable the sound?

---

### Post by DVSG on 2007-05-04
same problem here, did you find a solution so far?

---

### Post by teddmeister2 on 2007-05-07
I went to [http://www.frozen-bubble.org/](http://www.frozen-bubble.org/) and actually found this explicitly mentioned in the FAQ, so frozen-bubble apparently has this problem solved.
> Special keys

In the 3p/4p/5p network game, you can see F1, F2, F3 and F4 printed in the game screen - one function key per remote player. These keys allow you to aim at a particular remote player instead of everyone at the same time. Indeed, by default, when you create malus bubbles to be sent to your opponents (by exploding a larger group or when bubbles were sticked to exploding bubbles), they are distributed evenly among all of the (living) opponents. If you hit the, say, F2 key before (you can verify you did because the F2 key is then printed in white), next time you will create malus bubbles, they will all be sent to the top-right opponent. This feature can allow you to team up or to aim at the strongest opponent. You can hit F10 to request back an evenly distribution. Notice that when using at least version 2.1.0, you can see who's attacking you at any time by looking at at pinguins left to your igloo.

The function keys F11 and F12 are also useful (version 2.1.0 minimum): F11 allows to toggle music, and F12 sound (music plus effects). Additionally, keypad's minus and plus keys allow to alter sound volume. 

p.s.  I just tried this and it works.

---

### Post by teddmeister2 on 2007-05-07
I'm not sure how to fix the problem for gweled.  I don't know enough programming experience to delve too deeply into the source code, but I found an option that I could pass on the command line to disable sound, but I couldn't get it to work.  Here's a copy of my code and the output:
```
me@my-laptop:~$ gweled --usage
Usage: gweled [-?] [-?] [-?] [-?] [-?] [-?] [-?|--help] [--usage] [--gdk-debug=FLAGS]
        [--gdk-no-debug=FLAGS] [--display=DISPLAY] [--screen=SCREEN]
        [--sync] [--name=NAME] [--class=CLASS] [--gtk-debug=FLAGS]
        [--gtk-no-debug=FLAGS] [--g-fatal-warnings] [--gtk-module=MODULE]
        [--oaf-ior-fd=FD] [--oaf-activate-iid=IID] [--oaf-private]
        [--disable-sound] [--enable-sound] [--espeaker=HOSTNAME:PORT]
        [--version] [--sm-client-id=ID] [--sm-config-prefix=PREFIX]
        [--sm-disable] [--disable-crash-dialog]
        [--load-modules=MODULE1,MODULE2,...]
me@my-laptop:~$ gweled --disable-sound

```
(type gweled --help for more detailed list of these options)
when executing "gweled --disable-sound", the program opens up and has music and sound.  Am I entering it wrong, or misunderstanding what it does, or is it a bug in the program?

If it is a bug, then is the only way to do this to edit sourcecode and/or recompile it without the sound files?

---

### Post by teddmeister2 on 2007-05-07
I wrote a script and a desktop entry to give you the option of running gweled without sound.
Now, the script is NOT pretty, and basically just involves creating a backup directory for the sound files, removing them from their proper directory, and then executing gweled, after you quit gweled, it copies the files back to the gweled sound directory, so that on next run, if you pick the normal gweled icon, you'll get the game with sound and if you pick the other you'll get the soundless version.
And if the above hasn't already cleared this up for you, this is JUST A WORKAROUND, and not a fix to the game.  
(I'm actually not sure if the inability to control sound would count as a bug or not)
Hope somebody out there can benefit from this.

p.s. make sure you read the readme before you extract or anything.

---


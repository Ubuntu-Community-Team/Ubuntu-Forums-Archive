---
title: "Is it possible to boot a laptop to Ubuntu 10.04 and NOT have the bluetooth radio on?"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by rocksockdoc on 2011-04-24
Is there a way to boot Ubuntu 10.04 and have the bluetooth radio automatically turned off (but available to turn on if/when needed)?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189852&stc=1&d=1303622945[/IMG]

---

### Post by balta on 2011-04-24
Hi there, 
I'm not quite sure of this as in my laptop I do need to use the hardware switch to have ubuntu notice bluetooth but you can give this a try without messing up your pc in a un-revertible way ;)
I suggest you to remove the bluetooth manager from the startup applications, you can do this by going to
Main Menu > System > Preference > Startup Applications
Here you may try disabling the Bluetooth manager and reboot.
You can then use bluetooth from 
Main Menu > System > Preference >  Bluetooth

Let me know if this works!

---

### Post by Quackers on 2011-04-24
You can turn bluetooth off with the Startup Applications window.

---

### Post by rocksockdoc on 2011-04-24
> **balta said:**
> Main Menu > System > Preference > Startup Applications

Ah. Perfect. This worked like a charm!

After I rebooted, the bluetooth manager was gone from the desktop.

No sense in wasting laptop battery power for something I've never used (yet).

Thanks for being gentle with me. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189914&stc=1&d=1303663932[/IMG]

---

### Post by rocksockdoc on 2011-04-24
> **Quackers said:**
> You can turn bluetooth off with the Startup Applications window.

It's early in the game but for others who try this, it's not obvious (to me anyway) how to turn bluetooth back on once it's removed from the startup applications.

I'm not too worried about it, as if I really want bluetooth on, I can put it back into the startup applications and then I'm pretty sure it will work.

But, just for others to note, after removing the bluetooth manager from the startup applications, and then re-booting without the bluetooth manager on, when I 'tried' to turn it back on using the suggested method (see photo below), it just hung.

No big deal ... just so others are aware of this minor complication.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189917&stc=1&d=1303664887[/IMG]

---

### Post by balta on 2011-04-24
Glad it worked, and nice and useful pics by the way!
Now the right thing to do would be marking the thread as solved using the "thread tools" button just above your first post.
therefore other people can enjoy the solution!
Have a nice day.

---

### Post by Quackers on 2011-04-24
Don't remove it from startup if you may want to re-enable it. Just untick the box to its left.

---

### Post by rocksockdoc on 2011-04-24
> **balta said:**
> nice and useful pics by the way!

Thanks. I do try to make it easy for people to help me and for the resulting help to help others so that it's worth YOUR time to help people like me (who try to give back to the forum when and where we can).

The pictures are done with a combination of tools, based on advice here:

[LIST]
[*]Cropping:
[LIST]
[*][SOLVED] 			 			[What's the best (i.e., quickest and easiest) program to manually crop digital photos]("http://ubuntuforums.org/showthread.php?t=1570447&highlight=screenshot")
[/LIST]
[*]Resizing:
[LIST]
[*][COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How best to batch shrink JPEG file size (not pixels) to a given number of KBs?]("http://ubuntuforums.org/showthread.php?t=1720675")
[/LIST]
[/LIST]

[LIST]
[*]Editing: [COLOR=#980101]****[/COLOR][COLOR=#980101]****[/COLOR]
[LIST]
[*][COLOR=#980101]**[ubuntu]**[/COLOR] 			 			How to draw a circle in GIMP?
[/LIST]
[/LIST]
[]("http://ubuntuforums.org/showthread.php?t=1086589&highlight=screenshot")
[LIST]
[*]Arrows
[LIST]
[*][COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[What's a good curved ARROW drawing tool in Ubuntu (similar to Paint.NET on Windoze)?]("http://ubuntuforums.org/showthread.php?t=1575505")
[/LIST]
[/LIST]
 > **balta said:**
> Now the right thing to do would be marking the thread as solved using the "thread tools" button just above your first post.

Done. Thanks for the tip. And for the help!

---


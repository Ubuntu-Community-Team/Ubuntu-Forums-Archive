---
title: "Data files from Windows partition"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by anish on 2005-06-11
I've copied some picture and mp3 files from my Windows parition (mounted on /mnt and cp).  For some reason I cannot use these files.  I can't play the mp3s or view the pictures.

Try mounting your Windows partitions and copying some files and see if you can use them! Why does this happen? I need to be able to use all my Windows files in Ubuntu if I am to successfully convert!

Anish

---

### Post by Xian on 2005-06-11
[QUOTE=anish]For some reason I cannot use these files.  I can't play the mp3s or view the pictures.[/QUOTE]
What are you using to play the mp3 files, and further can you play ANY mp3s regardless of whether or not they came from your windows partition? What format are the pictures in and what are you attempting to view them with?

---

### Post by anish on 2005-06-11
Hiya Xian,

> What are you using to play the mp3 files...

I've tried with xmms. When I double-click the song in the playlist, nothing happens. Likewise, when I press the play button, nothing happens.  I've also tried with Totem Movie Player, and it shows the following error: 

[INDENT][I]Totem could not play 'file:///home/anish/Lethal B - Forward Riddim.MP3'.
Could not open vfs file "file:///home/anish/Lethal%20B%20-  -1.995995orward%20Riddim.MP3" for reading.[/I][/INDENT]

I tried opening the same file with Totem again, and the error message came up, but this time it said:

[INDENT]*Failed to open; reason unknown.*[/INDENT]

> ...and further can you play ANY mp3s regardless of whether or not they came from your windows partition?

*Anish downloads Pachabel's Canon from [http://www.paradise-engineering.com/pachabels-canon/](http://www.paradise-engineering.com/pachabels-canon/) *

Hmm it doesn't work but both xmms and totem are saying I need to configure things properly, i.e. the files seem accessible, it's just my settings that are wrong.  But with my Windows files, the data in them just doesn't seem accessible.

> What format are the pictures in and what are you attempting to view them with?

They're mostly jpeg files, some gif, some png.  I've tried opening them with the default picture viewer, Eye of GNOME, but the EoG window is blank (no picture displays).  I've also tried loading them into 'F-Spot Photo Album,' but all the thumbnails are blank, and when I double-click a picture, a big question mark is displayed.

What do ya reckon!?

Anish

---

### Post by Xian on 2005-06-11
Okay, I can play the Pachabel's Canon mp3 just fine in XMMS so we need to get your configuration set correctly. What is the output plugin that you are using in XMMS? Try setting it to ALSA and see if that makes a difference. You might also try setting up your sound according to this nice [How-To](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple).

As for the pics I'm stumped. I can use EOG to open jpg & png files from both my NTFS partition and within Hoary. Have you tried opening some downloaded web images for example in EOG? If the file format is the same then there shouldn't be an issue. It almost sounds like the files are corrupted or saved in some other type of native image format.

---

### Post by Xian on 2005-06-11
To set the output plugin in XMMS right-click on the interface and choose:

Options > Preferences > Audio I/O Plugins > Output Plugin
Select ALSA from the drop-down menu.

---

### Post by Xian on 2005-06-11
One last thing.....(sorry, things keep coming to mind)

Enable the 'Universe' repos in Synaptic and make sure you have the gstreamer0.8-plugins metapkg installed and that it includes the gstreamer0.8-mad library. When this is finished run this command from a terminal:

```
$ gst-register-0.8
```

---

### Post by anish on 2005-06-12
Thanks! Just needed to download the gstreamer plugins and killall esd, and Pachabel's Canon works. But mp3s from my Windows partition still don't work  ](*,) Maybe I need to chmod them? Thanks for your help though! Now all I need to do is figure out how to do [this...](http://ubuntuforums.org/showthread.php?t=40928)

Does anyone else have this problem with their Windows files?

---

### Post by shanghaipi on 2005-06-19
Yes, I have the same problem and have installed all the codecs from ubuntuguide.org.  Only, I'm using Kubuntu and Amarok.  Very strange indeed.

---

### Post by anish on 2005-06-21
It turned out that I needed to chmod all the files! Maybe that's what you need to do as well? I think it's because we copied them using the root terminal, and it seems that all file moving and copying operations done in a root terminal makes the files unreadable by all but root.

---

### Post by shanghaipi on 2005-06-21
Actually, I think my problem was rellatively different then yours.  I couldn't play mp3 files from a networked windows XP computer (which I had copied all my mp3s to so I could install Kubuntu again).  I tried to build a collection with amaroK on the windows XP computer and the mp3 files would not work.  Now, on a previous installation of Kubuntu amd 64, when I copied my mp3s from the XP comp to my linux comp, the mp3s still wouldn't work.  Now that I installed the 32bit kubuntu, and copied the mp3s on to my hard drive, the mp3s somehow work now.  So I guess that's a bug for the 64 bit ubuntu team to figure out (although I believe I'm one out of a lot to have this problem occur).  Glad you figured your problem out though.  I uninstalled the 64 bit version and went back to Windows because i couldn't use java, flash player, had problems with my printer connection and couldn't for the life of me, understand how to chroot or use 32 bit versions of java and the like.  I'm still very very new to linux and keep coming back to it becuase I love its community and its ideals (not to mention the OS is better, if you are nerdy enough to know how to use it).  But KDE and Gnome have a long way to go to capture those of us who aren't as geeky enough to experiment with Linux.

---


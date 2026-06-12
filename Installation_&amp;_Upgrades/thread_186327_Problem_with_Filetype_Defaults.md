---
title: "Problem with Filetype Defaults"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by snman31 on 2006-06-01
Hello, I just upgraded to Dapper from Breezy, and everything is fine with the following exception. When I try to play an mp3, I get the following error message:

****************************
The filename "Artist - Title.mp3" indicates that this file is of type "mp3 document". The contents of the file indicate that the file is of type "MP3 audio". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "MP3 audio", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 
****************************

When I select "open with" and choose Totem or Rythmbox or anything else, it plays just fine. However, when I double-click on the file again, I get the same error message.

How can I permanently associate this filetype with a given application? All the posts I searched said to use "open with" but that isn't working. Also, what does the error message mean anyways?

Thanks in advance for the help.

---

### Post by llamakc on 2006-06-01
apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

and make sure the universe/multiverse are in your /etc/apt/sources.list

---

### Post by snman31 on 2006-06-01
Did the above, but the problem persists. I don't think the problem was with gstreamer, though, as the file will play just fine if I select "open with" and any audio player, however it won't play on double-click no matter how many times I tell it to open the file with a given player.

Any other ideas?

---

### Post by llamakc on 2006-06-01
Can you now play it with alsaplay or mpg123 from the commandline? My daughter's Dapper box recently had the same issue. Since she uses Gnome exclusively I added the packages and made her logout/login.

Worked just fine after that. I may have ran gst-register-0.8 but I don't remember.

So its a double-click from Nautilus issue?

---

### Post by snman31 on 2006-06-01
I can play from commandline with mpg123 just fine. I tried ctrl-alt-bksp and re-logging in, and that didn't work. I also tried gst-register-0.8 at your suggestion but still no dice. Same error message.

It is a double-click from Nautilus issue, yes. Any more ideas are appreciated, and thanks so much for taking the time.

---

### Post by llamakc on 2006-06-01
I'm a recent Breezy-to-Dapper dist-upgrade person and I can browse music files in Nautilus and the sound-preview works, also double-clicking brings up Totem and the files play.

I dunno enough to help you anymore with Nautilus.

---

### Post by snman31 on 2006-06-01
Well it's good to know it's possible to make it work, I just wish I knew how :) Thanks for letting me know I'll get it working eventually though.

---

### Post by llamakc on 2006-06-01
I don't use Nautilus too extensively so I never bothered with tweaking it. Perhaps moving your ~/.nautilus to ~/.nautilus-backup and relogging in to see if that fixes it? I see there are files in ~/.gnome2/nautilus-scripts also.

---

### Post by snman31 on 2006-06-02
Deleting and re-logging in didn't seem to do anything. However while messing around I found that if I change my music files to .MP3 instead of .mp3 they play on double click. I'd rather not have to change every extention for all my files, though.

---

### Post by llamakc on 2006-06-02
Do you have this line in /etc/mime.types:

ken@vulva:~$ cat /etc/mime.types | grep mp3
audio/mpeg                                      mpga mpega mp2 mp3 m4a

---

### Post by snman31 on 2006-06-02
Yes, that line is in there. Do I need to activate the file somehow?

---

### Post by meng on 2006-06-03
I'm having exactly the same problem, except with .exe windows executables, which won't open with Wine. A very similar warning message about security risk comes up, and my mime-types files look completely correct. If I rename to .EXE they will work (temporarily). If I can find out what the problem is on my system, it should be the same as on yours.

---

### Post by meng on 2006-06-05
Other folks with similar problems seem to have solved it by rm -rf ~/.local/share/mime

I can report this also worked for me.

If you're paranoid (like me) you can back up that directory before you delete it. It oughtn't break your system, but it never hurts to be too careful.

EDIT: clarification - I actually deleted ~/.local entirely. Incomplete removal did not work. I then had to reset some default apps.

---

### Post by arkangel on 2006-09-01
rm ~/.local/share/mime 

solved my problem  , with the mp3 files as described for owner of this thread

---

### Post by Teebs01 on 2007-04-04
In the text file ~/.local/share/mime/globs I found the line

application/x-extension-mp3:*.mp3

The globs file comes with a large warning at the beginning not to edit it. After blatantly ignoring this warning, I deleted the above line, and it seemed to fix the problem (I was having exactly the same problem as snman). I would highly recommend making a backup of globs before you try this, just in case the warning is there for a good reason, but I'm not having any problems with it (yet).

My best guess is that this line associated anything ending with .mp3 with the mime type "application/x-extension-mp3" instead of the correct type "audio/mpeg" (in my /etc/mime.types I found the line "audio/mpeg mp3" which I can only assume correctly associates mp3 documents with the "audio/mpeg" type -- I guess the contents of ~/.local/share/mime override /etc/mime.types?). This is all just conjecture; I may be completely wrong. If anyone knows more about this, I would love to hear how it all works.

Hope this helps!

---


---
title: "Rar"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by The Noodlez on 2007-10-09
I downloaded RAR but do not understand how to install it...
I used 'sudo apt-get install rar' when I couldn't figure out the installer I downloaded, and it said it worked fine, but I don't see it anywhere.
Does it have a graphic interface?

---

### Post by ryanVickers on 2007-10-09
[B][SIZE=5]use my rar maker!!! ;) (signature)

[SIZE=3]This is like the whole reason I made it!!! :p[/SIZE]
[/SIZE] 
[/B]it automatically installs RAR, UNRAR, anything else you may need (if not already installed), and then lets you make RAR's **sooo** easily! ;)

I know the command is a real mess, so that;s why I made it.  Just download the archive, extract it, and it should just run in the terminal on click (if not, set it to be executable)

---

### Post by The Noodlez on 2007-10-09
When you click it, should it do something? Because it does nothing for me...
Does it have a interface like in windows?

---

### Post by ryanVickers on 2007-10-09
OK, here are the [screenshots]("http://www.mediafire.com/?f9lylestjsm").

You should just be able to download the archive (attached at the bottom), extract it, and then click on "mkrar.sh" and pick "run in terminal"

If you still can't get it - here's video instructions (attached) ;)  Just download, extract, play, learn, and do!

---

### Post by The Noodlez on 2007-10-09
im a fool... lol I didn't see what you put in bold...

---

### Post by ryanVickers on 2007-10-09
Did you get it working (I posted above your post before you were done...)

---

### Post by The Noodlez on 2007-10-09
I installed it and when I tried to create an archive it failed...
Is there nothing as simple as winrar?

---

### Post by ryanVickers on 2007-10-09
There is just one rule - make sure that the file/folder you are archiving does not have a space in the name! ;)  If it's a folder, the contents can have spaces, just not the folder itself - If this was the problem, just rename it temporarily...

recommendation - use the drop down menus to pick a file/folder - It will check if it exists (in case of typos) but also just look yourself - make sure it does not have a space (or in the event of using the menus, it will split up one folder name (with spaces) into many entries - pick a REAL one! ;))

---

### Post by The Noodlez on 2007-10-09
how hard would it be to make your program the way it is, but with a window interface and tabs or dropdown boxes for all the options instead of the many many windows...

---

### Post by ryanVickers on 2007-10-09
Quite hard actually ;)

I use zenity, which can pop up lots of dialogs, but one window is impossible with it as far as I know.  Of course, there are lots of other tools out there, like python, C (++), and QT, but I like to stick with my strengths (bash ;)

---

### Post by The Noodlez on 2007-10-09
well crap... why is it that they release winrar, with a graphic interface, for windows, but for linux, all we got was a command line thing...
This sucks...

---

### Post by ryanVickers on 2007-10-09
when you installed rar, it should have also added it on to file roller. explanation: you can right-click on any folder or group of folders /files and click make archive or something, and then pick rar from the list instead of the default tar.gz...  This does not allow you to set other options, compression level, splitting etc. though :(

I've never had a problem with my script, but if those extra windows is just so horrible that your willing to give up all the features and go to file roller, then ok... ;)

---

### Post by The Noodlez on 2007-10-09
i know, it is added to the file roller, but i needed the split archives...
I deal with a lot of large files and distribute them, but I have no dvd burner so i usually have to put them on multiple disks or upload them in splits...

---

### Post by The Noodlez on 2007-10-09
Well I have it now... I'll use it when the need arises...
Thanks, it's a lot better than nothing...
BTW, how does it do compresising multimedia?

---

### Post by ryanVickers on 2007-10-09
I've found that avi, mpeg, ogg, etc. don't really compress at all, but .wav tends to do quite nicely...

Edit: Just make sure that you know that "rar" is doing the compressing and my script just puts the command together ;), so if it doesn't compress very well, don't blame me! :p

If you want to split something up but not compress it (in the even that compressing it would be pointless), just set the compression to zero to just archive it - it's way faster!!

---


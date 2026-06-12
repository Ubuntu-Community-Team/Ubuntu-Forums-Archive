---
title: "I know, I know, but..Screensaver &quot;Pictures folder&quot; does not use &quot;Pictures&quot; folder..."
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-12
...when it is being selected!  In my case I get my folder called "MRK_Images_Misc" displayed.  It DOES, however, display the correct "Pictures" folder when it activates.

Anyone else?

---

### Post by ranch hand on 2009-10-12
Where in tarnation is this MRK_Images_Misc file?

I have never seen it and I have had a search for it going for 5 minutes in nautilus and it hasn't found the bugger.

---

### Post by emarkay on 2009-10-12
> **ranch hand said:**
> Where in tarnation is this MRK_Images_Misc file?
 I have never seen it and I have had a search for it going for 5 minutes in nautilus and it hasn't found the bugger.

Thats MY folder name - I just mentioned it because that's where it went - in the case that something in that filename is a "no-no" or something  :)

Can you put some photos in "Pictures" and create anothe folder and then confirm the SS work OK, but the config window shows the other file's contents?

---

### Post by ranch hand on 2009-10-12
I don't know.  I am sure that if you dig into the code you sure could.

---

### Post by emarkay on 2009-10-12
> **ranch hand said:**
> I don't know.  I am sure that if you dig into the code you sure could.

I am not a programmer.  :)

---

### Post by jongkind on 2009-10-13
By following these steps you can specify which picture folder to use:

[LIST]
[*]gksu gedit /usr/share/applications/screensavers/personal-slideshow.desktop
[*]Scroll down to the line (near the end) that begins: Exec=slideshow
[*]Add the following after this command: --location=<your pictures path>
[/LIST]

grtz, Herman

---

### Post by ranch hand on 2009-10-13
Oh wow.  That is cool.  Going to do that myself just for FUN.

Is Linux great or what?

---

### Post by blur xc on 2009-10-13
> **ranch hand said:**
> Oh wow.  That is cool.  Going to do that myself just for FUN.

Is Linux great or what?

<sarcasm?>

I won't argue there, I love my Ubuntu flavored Linux- but I don't think it's great that I have to get frustrated, ask on a forum, edit some obscure text file to add what path I want it to look for my screen saver folder, when I can click one or two buttons on my almost 10yr old operating system to do the same thing.

I went through this same ordeal a while back.  As an amateur photog, it's important for me to have my slideshow screensaver.  It's a great conversation starter when people are over.

BM

---

### Post by ranch hand on 2009-10-13
Well, you sound a little disgruntled.

If you try this in an older Ubuntu, say 9.04, you will have a harder time of it.

Linux has a tendency to go for core functionality first.  Eye candy later.  While I can see your point, I think this is the right way to do it.

Could, easily, set up a directory of photos and run a slide show for the same purpose.  I used my "Pictures" file as the place to put what I wanted displayed and simply had (have) a Photo directory for my storage.  This is not hard.

No, it is not Win Jerry Lewis Pro.  I assume there is some reason that you are not running that and have gone to Ubuntu.  I know there is for me.

---

### Post by blur xc on 2009-10-13
> **ranch hand said:**
> Well, you sound a little disgruntled.

If you try this in an older Ubuntu, say 9.04, you will have a harder time of it.

Linux has a tendency to go for core functionality first.  Eye candy later.  While I can see your point, I think this is the right way to do it.

Could, easily, set up a directory of photos and run a slide show for the same purpose.  I used my "Pictures" file as the place to put what I wanted displayed and simply had (have) a Photo directory for my storage.  This is not hard.

No, it is not Win Jerry Lewis Pro.  I assume there is some reason that you are not running that and have gone to Ubuntu.  I know there is for me.

I thought of that, having my pictures folder for my screen-saver photos, and another for random images, etc...  But- My wife and I have our own user accounts, and we use the same screen saver slide-shows for both our user accounts.  The other thing is that apps that capture screen images, download from the internet, etc., default to the pictures folder, and then I'd have to navigate to another folder to not pollute my screen-saver folder.  I know there are work-a-rounds, but the best way is to use whatever folder I want for my screen-saver, which happens to be on an external drive, with the rest of our photos.  Eventually, they will be on a file server...

BM

---

### Post by emarkay on 2009-10-13
Still want to know if this is a BUG or not - my NVIDIA pc is OK.

---

### Post by ranch hand on 2009-10-13
Gee whiz, I had to go back to see what we are supposed to be discussing.  OOPS.

I think it is a bug.

---

### Post by emarkay on 2009-10-15
Bug filed:
[https://bugs.launchpad.net/ubuntu/+bug/452465](https://bugs.launchpad.net/ubuntu/+bug/452465)

---

### Post by emarkay on 2009-10-16
I confirmed that it's not the "special" icon on the Pictures directory, either.


 I made a new folder and hid it and placed all my images in there, to try to see if that solved this, and yes it did, but then, it goes down into all the directories and was displaying old images from about 4 levels down in an archived directory of mine!

If you could test this, and if it affects you , can you confirm on the bug report?

---

### Post by mgmiller on 2009-10-16
Here is a link to a quick and easy guide to give you full gui control over your screensavers again.  It is written for Intrepid, but I am using it in both Jaunty and Karmic.  It works fine and lets you specify the default folders for pictures and lots of other stuff:
[http://maketecheasier.com/edit-your-screensaver-settings-in-ubuntu-intrepid/2009/03/07](http://maketecheasier.com/edit-your-screensaver-settings-in-ubuntu-intrepid/2009/03/07)

Note the path to the Pictures folder is set from the "Advanced" tab.

---

### Post by emarkay on 2009-10-16
> **mgmiller said:**
> Here is a link to a quick and easy guide to give you full gui control over your screensavers again.  It is written for Intrepid, but I am using it in both Jaunty and Karmic.  It works fine and lets you specify the default folders for pictures and lots of other stuff:
[http://maketecheasier.com/edit-your-screensaver-settings-in-ubuntu-intrepid/2009/03/07](http://maketecheasier.com/edit-your-screensaver-settings-in-ubuntu-intrepid/2009/03/07)
 Note the path to the Pictures folder is set from the "Advanced" tab.


OK that's cool, but that doesn't explain why this is an issue; why it's AFU here on a fresh install.

ALSO my other 2 PC's, after observation do NOT have this problem!

---

### Post by mgmiller on 2009-10-17
> OK that's cool, but that doesn't explain why this is an issue; why it's AFU here on a fresh install.

This is a beta.  It's for testing and bug reporting to help make the final release as smooth as possible.  Did you report the problems you encountered?

---

### Post by emarkay on 2009-10-17
Yes see post #13.
[https://bugs.launchpad.net/ubuntu/+bug/452465](https://bugs.launchpad.net/ubuntu/+bug/452465)
I  want to get any additional info here for those that may not use Launchpad, so I can add it there.

---

### Post by mgmiller on 2009-10-17
> Yes see post #13.

Oops, I'm usually more observant than that.  Thanks for filing the bug report.

You imply that you have 3 PC's.  Are all 3 running Karmic?  Are they all 32 or 64 bit?  Are they all up to date?  Were they all fresh installs or were some upgrades?

---

### Post by emarkay on 2009-10-17
All are updated to today, all are 32 bit, all are fresh installs - this is what's so bizarre.  I mean this PC (the Nvidia desktop) is picking up jpegs from all OVER (OOPS, SORRY MOMMY!)** over** my machine! 

Like I said, it's only a screen saver, but this is weird.  I think I will reload this one when the RC is released and see if it still is doing this.

Thanks!

---

### Post by jongkind on 2009-10-18
> **emarkay said:**
> I think I will reload this one when the RC is released and see if it still is doing this.

That will not help. Best solution for me is mentioned in post #6 of this thread.

---

### Post by aamukahvi on 2009-10-18
Have you checked if your xdg user dirs are in order? They might be related to your problem.

Note that you can also use this file to change the default Pictures folder to whatever you want.

they're configured in ~/.config/user-dirs.dirs and the contents should be something like this:
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by emarkay on 2009-10-18
Hmm - I get:

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"

Not what I want - will change "XDG_PICTURES_DIR="$HOME/" to XDG_PICTURES_DIR="$HOME/Pictures"

Thanks - will also note this on the Bug report.

---


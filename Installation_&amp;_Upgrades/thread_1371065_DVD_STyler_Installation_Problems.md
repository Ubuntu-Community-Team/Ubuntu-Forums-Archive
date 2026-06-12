---
title: "DVD STyler Installation Problems"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by bugs2beatles on 2010-01-03
Hi Guys,
              This is my first time here. I have used Ubuntu 9.04 before, but with the help of a Ubuntu familiar Techno guy. Now I 'm on my own. I installed Ubuntu 9.10 as soon as i recieved it by mail from canonical. Everything went fine. Now I want to Install either Devede or DVD styler or qdvdauthor. But all of them fail to install citing dependancies problem. I did not have these issues when I installed Devede on 9.04. I badly need a good DVD authoring software and DVDflick (in Wine) Simply doen't run on my comp. I have a Pentium 4, i686, Mercury Motherboard Set with a Dell Monitor. I have listed word to word of each and every  installation failure messages and posted here for your perusal. On all accounts I'm a novice. So would be grateful to anyone who could guide me through step by step procedure of circumventing this problem. (Remember, I don't understand much of the terminal stuff either)..Please..Please Guys...

[FONT=Fixedsys][SIZE=2]_**dvdstyler**_:
Depends: dvdauthor but it is not installable
Depends: mjpegtools but it is not going to be installed
Depends: libavcodec-extra-52 but it is not going to be installed
Depends: libwxsvg0 (>=1:1.0) but it is not installable
Recommends: xine-ui but it is not installable
Recommends: dvdisaster but it is not installable

_**devede**_:
Depends: dvdauthor but it is not installable
Depends: vcdimager but it is not going to be installed
Depends: libavcodec-extra-52 but it is not going to be installed
Depends: libavformat-extra-52but it is not going to be installed

_**qdvdauthor**_:
Depends: dvdauthor (>=0.6.10) but it is not installable
Depends: mjpegtools but it is not going to be installed
Depends: sox but it is not going to be installed
Depends: videotrans but it is not going to be installed
Depends: dvd-slideshow but it is not going to be installed


[FONT=Verdana]Please Somehow give me a work around....
[/FONT]
[/SIZE][/FONT]

---

### Post by lidex on 2010-01-03
Go to your Applications menu. "System>Administration>Software Sources". On the first tab, "Ubuntu Software", make sure you have a tick in the first four boxes. Close that and allow to update.

Now in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras medibuntu-keyring

```

---

### Post by bugs2beatles on 2010-01-03
> **lidex said:**
> Go to your Applications menu. "System>Administration>Software Sources". On the first tab, "Ubuntu Software", make sure you have a tick in the first four boxes. Close that and allow to update.

Now in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras medibuntu-keyring

```
Hi Lidex....Thanks a million. It worked wonders. Now I can put my trust back into the Ubuntu lineage...
Thanks...And Wish you a Happy New Year...:-)

---

### Post by lidex on 2010-01-03
> **bugs2beatles said:**
> Hi Lidex....Thanks a million. It worked wonders. Now I can put my trust back into the Ubuntu lineage...
Thanks...And Wish you a Happy New Year...:-)

You're welcome!;)

---

### Post by bugs2beatles on 2010-01-12
> **lidex said:**
> You're welcome!;)
Hi Lidex,
 I use Ubuntu Karmic Koala 9.10 on my P4, 256 MB RAM, 80 GB SATA HD, DELL Monitor. Its been working fine till today morning. After a restart, My Desktop Wallpaper was gone. Instead there was a blank White Screen and further, all the icons in the Desktop folder were lined up against the White background. and finally I got an Error message as below. The Transmission program now fails to download anything as I keep getting an Error message saying "Can't find Download Folder". Where in fact Downloads folder is very much there in the Places button. Lastly, The Desktop folder is empty. The entire Desktop feel & Customisation is gone. poof...!! I really don't know much about Terminal stuff. So If anyone could kindly guide me through step by step of the whole workaround I would be extremely grateful. PLEASE. PLEASE....


**COULD NOT DISPLAY "x-nautilus-desktop:///**".
Error: DBus error
org.freedesktop.DBus.Error.ServiceUnknown: The name
org.gTk.vfs.Daemon was not provided by any .service files
Please select another viewer and try again.

So that was the error I got. Restarts just don't help. All other settings remain. Except personal Desktop Environment preferences aka Wallpaper, icons within the Desktop folder and last but not least, all these icons from Desktop folder being clumped around each other against the blank White Screen...Please help..I've attached a screen shot of the error message as well..:smile:
 		                   		 		 			  			 				 					Attached Thumbnails 					 					 [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142973&stc=1&thumb=1&d=1263017690[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=142973&d=1263017690")

---

### Post by lidex on 2010-01-12
bugs2beatles;
You really should open another thread for this new problem.

Run these commands in a terminal:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
mv .gnome2 .gnome2OLD
```
```
mv .nautilus .nautilusOLD
```
```
sudo apt-get remove --purge nautilus && sudo apt-get install nautilus
```

In order please, then reboot.

---

### Post by bugs2beatles on 2010-01-17
Hi Lidex,
              Let me first thank You profusely for your timely intervention. I would like to clarify that in fact a week or two back, I had posted this very question as a brand new thread under Desktop Environments Forum. For days I waited. Lots and Lots of people viewed it, but none replied to it. With no other choice I came back to you. Anyway many thanks again...
-bugs2beatles :-)

---


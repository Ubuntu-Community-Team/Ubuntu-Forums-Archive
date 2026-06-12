---
title: "manual recovery"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by helphelp on 2011-05-16
Hi
I was upgrading for 10 10 to 11 04. The message i'm getting is 
The disc drive for / is not ready or present
continue to wait or press s to skip mounting or m for manual recorvery
Does anyone know how i can do a manual recorvery

---

### Post by Rubi1200 on 2011-05-17
Hi,
we need to get a better overview of the current state of the system.

Please do the following from a LiveCD/USB:

1. download this script [BIS-2]("http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;%20hb=HEAD")

2. move it to the desktop on the live medium

3. run this command in the terminal:

```
 sudo bash ~/Desktop/boot_info_script*.sh 

```This will create a RESULTS.txt file on the desktop.

Copy/paste the contents into a new post. Once pasted, highlight all the text and click on the # icon on the toolbar to wrap the text with code tags.

Thanks.

---

### Post by helphelp on 2011-05-17
Hi, 
Thanks for that, i'm not too sure about  this bit   ( Copy/paste the contents into a new post )
Should i post the contents in a thread?
Just out of curiosity would a technically qualified person be able to manually repair a computer from the option press m for manual recovery.
I will get a live cd  and do what you suggested .I have never used a live cd before, i don't have  
a lot of information on the o/s .Would it be possible to copy what i need on a usb and just do a new install.

---

### Post by Rubi1200 on 2011-05-17
> **helphelp said:**
> Hi, 
Thanks for that, i'm not too sure about  this bit   ( Copy/paste the contents into a new post )
Should i post the contents in a thread?
Just out of curiosity would a technically qualified person be able to manually repair a computer from the option press m for manual recovery.
I will get a live cd  and do what you suggested .I have never used a live cd before, i don't have  
a lot of information on the o/s .Would it be possible to copy what i need on a usb and just do a new install.
 > i'm not too sure about  this bit   ( Copy/paste the contents into a new post )
Should i post the contents in a thread?
Once you have run the script as I instructed it creates a text file which you then open. Copy the contents into a new post in this thread and paste the contents there.

Get hold of a LiveCD/USB. Instructions here on how to create the CD/USB too:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

You could reinstall if you wanted, but wouldn't you rather try and repair it first?

By the way, if you don't have a CD how did you install in the first place?

---

### Post by helphelp on 2011-05-18
synaptic package manager.
I've tried a few times to burn a live cd without success.  I 'm not sure if it's the quality of cd i'm using or the download. I 'm  not too sure about doing the checksum on the download ( do you get the information from the download page if so i can seem to locate it, or from a file within the download?
I will get myself a live cd  from  a shop

---

### Post by helphelp on 2011-05-20
Hi
I got myself a live cd.I cannot get it to load. 
(operating system not found  is the message}
Any idea what would cause this ?

---


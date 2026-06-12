---
title: "How Do I Test 12.10?"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by Smallwheels on 2013-01-01
I've got the live CD in my computer. I tested the printer connection and it is recognized. I did not try to print a page because the printer is out of ink. 

One problem is that I need a scanning program to interface it with Ubuntu. It works in 10.04. I can't test that in the live CD, or can I? 

I went to the web and I'm connected. I wanted to watch a Youtube video and it says I need Flash. How would I test 12.10 without it? 

I made a test file of different things on my other computer. It has an Open Office file, an image file, a video file, and an RTF document file. I loaded this folder on my external hard drive. Then I connected the external hard drive to the Linux computer. The device was recognized and I had access to the files. 

The video wouldn't play because I need a plugin. 

The RTF file opened with Libre Office. So did the Open Office file. What I found was I can't edit either file. If I transfer all of my files to the external device in order to access them on the Ubuntu 12.10 computer, I definitely will want the ability to modify them. How can I do that? There must be a way. 

I also tried creating a new file in Libre Office. I then tried to save it to my external hard drive. It would not work. I could name the file and click save but the program gave me a message Error saving the document:

 "Untitled 1:/media/ubuntu/Tons of numbers and letters/Test File Mac To Linux/External Hard Drive File.odt does not exist."

The document wasn't untitled. I did name it. All of those numbers and letters were entered into the file path by Ubuntu. In the dialog window I did select the external hard drive and then the folder where I wanted it to go. When clicking Save, it gave me the above message. 

My goal is to make 12.10 work so I can use the new program to make Netflix work on Ubuntu. Then I want to migrate all of my Windows Files and Mac Files to my external hard drive so I can access them with Ubuntu 12.10. Once everything is working I'll sell the Mac to get some extra money and buy another used computer to keep as a spare. 

This wonderful plan all depends on getting 12.10 working and being able to read and change existing files from those other machines. If I can't edit existing documents then it would be too much work to retype and reformat each file individually. There must be a way. 

First things first. I need to verify that the features of 12.10 work. 

I'll need for the videos to be able to play and the scanner to work. Can these be tested in the Live CD? 

Thank you. 

Michael

---

### Post by Smallwheels on 2013-01-01
I found a way to test the scanner. So that problem is handled.

Michael

---

### Post by oldos2er on 2013-01-01
> **Smallwheels said:**
> I made a test file of different things on my other computer. It has an Open Office file, an image file, a video file, and an RTF document file. I loaded this folder on my external hard drive. Then I connected the external hard drive to the Linux computer. The device was recognized and I had access to the files. 

The video wouldn't play because I need a plugin. 

The RTF file opened with Libre Office. So did the Open Office file. What I found was I can't edit either file.

Probably because the external device was mounted read-only. You'd need to mount it with read-write permissions to edit and save files on it.

Proprietary video codecs (including flash) are not included on Ubuntu Live images for legal reasons. If you have enough RAM you should be able to install and use them (although I have never tried this myself). See [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Smallwheels on 2013-01-01
> **oldos2er said:**
> Probably because the external device was mounted read-only. You'd need to mount it with read-write permissions to edit and save files on it.

Thank you for that tip. How do I do that?

---

### Post by oldos2er on 2013-01-01
Is it NTFS?

---

### Post by Smallwheels on 2013-01-01
> **oldos2er said:**
> Is it NTFS?I don't know. When I bought the external hard drive it was formatted to work with my Mac Book. It came from G-tech. 

If I right click on the icon of the drive while it is connected to the Mac Book and select Get Information, the format says Mac OS Extended (Journaled).

---

### Post by oldos2er on 2013-01-02
So I'm guessing it's HFS then? Maybe something in this thread will help: [http://ubuntuforums.org/showthread.php?t=1670991](http://ubuntuforums.org/showthread.php?t=1670991)

---

### Post by Smallwheels on 2013-01-02
Thank you. I'm going to read this and study it. I'm not certain it is the total solution. I'll post again when I understand exactly what this can do and if it solves my current needs. Most likely I'll be asking more questions.

Michael

---


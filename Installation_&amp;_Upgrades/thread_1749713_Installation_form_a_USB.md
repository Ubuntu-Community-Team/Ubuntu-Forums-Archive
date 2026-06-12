---
title: "Installation form a USB"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by orbitpilot on 2011-05-04
So i installed Ubuntu and i love it, i restarted the laptop (Dell M1330 XPS) and now it gives me "No Default or UI configuration directive found
Boot: " the usb is removed. is that why?

So do i always need to have the Flash drive in?

---

### Post by oldfred on 2011-05-04
Does your system promote the USB flash to sda when plugged in? Grub normally defaults to install to sda.

To see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If you installed Natty download this version. Instructions are in above link.
Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

---

### Post by Dutch70 on 2011-05-04
Hi and welcome to UF

No, you don't need the usb stick in after you install Ubuntu.
Can you give some more details please?
Edit: Yeah, that info oldfred asked for will work. ;)

Give this a quick read first.
[[COLOR="Red"]how to get your support questions answered as quickly as possible[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by orbitpilot on 2011-05-04
> **Dutch70 said:**
> Hi and welcome to UF

No, you don't need the usb stick in after you install Ubuntu.
Can you give some more details please?
Edit: Yeah, that info oldfred asked for will work. ;)

Give this a quick read first.
[[COLOR="Red"]how to get your support questions answered as quickly as possible[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

Thanks guys, got it to work. Just changed boot from USB to HDD first. Anyways. next problem

WIRELESS

i just installed the drivers for it, restarted, now the "wireless network" option is gone from the dropdown

---

### Post by Dutch70 on 2011-05-04
Glad you got the booting part worked out anyway. 

It would still be a good idea to read the link I gave you if you're going to start a thread for your wireless.

Don't forget to mark this thread "solved" with "Thread Tools" at the top of the page. :)

---

### Post by orbitpilot on 2011-05-04
> **Dutch70 said:**
> Glad you got the booting part worked out anyway. 

It would still be a good idea to read the link I gave you if you're going to start a thread for your wireless.

Don't forget to mark this thread "solved" with "Thread Tools" at the top of the page. :)

Will do, Thanks much!

EDIT:

After reading through i had discovered my question goes unanswered. :(

---

### Post by orbitpilot on 2011-05-04
anyone? any ideas?

---

### Post by Dutch70 on 2011-05-04
I thought this was already marked solved? :confused:

---

### Post by orbitpilot on 2011-05-05
> **Dutch70 said:**
> I thought this was already marked solved? :confused:

only if. i have another thread rocking out with this. but, they are having me run terminal coding, and other stuff i dont understand yet (i was a vista man) and im starting to like their coding. anyway. you have anythoughts?

---

### Post by Dutch70 on 2011-05-05
No, and if I did, I would have posted it in your other thread. 

The chances of you getting answers to a wireless problem inside a thread titled *"installation from a usb"* are kind of slim. 

Also, you may have people clicking on and reading through this thread to try and help with your installation problem, only to find out that you've already solved the issue. 
Just a fair warning. That usually doesn't sit well with people.

---


---
title: "Can't find Ubuntu 12.04 on boot menu"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by pineappleeater on 2012-06-01
So I installed Ubuntu 12.04 alongside Windows XP on my netbook via a usb (since it doesn't have a DVD/CD drive).


  At the end of the installation, I got an error saying the bootloader  couldn't be installed, but I selected the hard drive and everything  seemed ok.


  However, whenever I turn on the computer, it goes straight to Windows  XP. And when I go to the OS selection screen during startup, Ubuntu is  not there.


  I heard that you can fix this problem through booting up Ubuntu again  with the flash drive. However, when I boot through the flash drive, it  gives me the options of trying without installing, installing, etc. 



  I really have no idea where to go from here, can anyone please help out?  Thanks!

---

### Post by wilee-nilee on 2012-06-01
Use this tool, when run, on the first gui that shows, hit the bootinfo summary button. It will run then give you a HTTP address where it is at, post that address. We will probably use the tool to fix your set up, just so you know.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by pineappleeater on 2012-06-01
> **wilee-nilee said:**
> Use this tool, when run, on the first gui that shows, hit the bootinfo summary button. It will run then give you a HTTP address where it is at, post that address. We will probably use the tool to fix your set up, just so you know.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


By "First GUI that shows," do you mean Windows?

Or do you mean running it through Ubuntu? (running it from flash drive, then installing boot repair via Terminal)

(And yes, I am a complete newbie :/)

---

### Post by wilee-nilee on 2012-06-01
> **pineappleeater said:**
> By "First GUI that shows," do you mean Windows?

Or do you mean running it through Ubuntu? (running it from flash drive, then installing boot repair via Terminal)

(And yes, I am a complete newbie :/)

Go to the link, it explains a download to a ubuntu live cd, a actual ubuntu install, or a cd to download. The first picture of the tool on that page shows the bootinfo summary button.;)

You might just download the cd it is a great tool worth having, and it can be loaded to a usb/flash with unetbootin as well to boot to the app. 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by pineappleeater on 2012-06-01
Hmmm....

I tried the boot repair, but it unfortunately did not  work. I did the installation via terminal, but typing "boot-repair" to  launch it via terminal brings the message "command not found"


grrr

---

### Post by wilee-nilee on 2012-06-01
> **pineappleeater said:**
> Hmmm....

I tried the boot repair, but it unfortunately did not  work. I did the installation via terminal, but typing "boot-repair" to  launch it via terminal brings the message "command not found"


grrr

Hmm I guess I did not make it clear enough the importance of that bootinfo summary script. Slow down, read what I have posted, and do what you think is appropriate. I did not tell you to run it, but to generate the debugging script and to post the http address.

You actually have already run the script it runs automatically unless you turn it off, post the http address of where the script is.

---

### Post by pineappleeater on 2012-06-01
Ah, I guess I'm just having trouble understanding what you mean. I ran the installation text on terminal and it gave me a bunch of text, but no url. Is that as far as you needed me to go? Or do I need to run it by entering boot-repair in terminal (which didn't work as well).


Bleh it must be cuz it's getting a bit late. Maybe I'll give it a shot during the day.

Thanks though!

---

### Post by wilee-nilee on 2012-06-01
> **pineappleeater said:**
> Ah, I guess I'm just having trouble understanding what you mean. I ran the installation text on terminal and it gave me a bunch of text, but no url. Is that as far as you needed me to go? Or do I need to run it by entering boot-repair in terminal (which didn't work as well).


Bleh it must be cuz it's getting a bit late. Maybe I'll give it a shot during the day.

Thanks though!

If you used the terminal it was to install the repository link for the tool, and to install it if run correctly. It would then be a application that opens with a gui.

But even better since we are trying to get the bootscript, down load it from the link using a ubuntu live cd/usb flash. Click the zipfile and extract it to the desktop and run the command in the terminal. 

A results.txt will appear on the desktop, open it and copy all the text and paste it to a reply . After pasting all the text highlight it and then click on the # in the reply panel, then submit the reply.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```To be honest this is the way I previously asked to get a copy of this script, but the tool has become popular so I have tried to just adapt. It can be confusing though so hopefully this second method makes more sense. ;)

---

### Post by pineappleeater on 2012-06-01
Thanks, I'll definitely give it a shot this weekend!

Luckily this is for my old backup netbook so it's not an urgent/emergency situation...

---

### Post by wilee-nilee on 2012-06-01
> **pineappleeater said:**
> Thanks, I'll definitely give it a shot this weekend!

Luckily this is for my old backup netbook so it's not an urgent/emergency situation...

Cool. ;)

---


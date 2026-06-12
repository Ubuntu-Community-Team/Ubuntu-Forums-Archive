---
title: "Cant Install Ubuntu on Old PC"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by dmelendez34 on 2010-12-15
I am trying to install Ubuntu 10.10 on my parent-in-laws old emachines computer (Celeron processor, 512mb RAM, 80GB HDD).  

I have installed it on a laptop, netbook and desktop without any problems but now that I am trying on their computer I get this message when the CD boots:

[0.024000] Kernel panic - not syncing: IO - APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option.

I have looked through various forums but I have not found a way around this install problem.  I have even tried installing the netbook edition, and Xubuntu but both of those boot CDs give me the same error.

One forum thread said to hit Esc before the disc gets to that error so I can run some commmands but any command I try gives the the message 'Linux not found' (or something along those lines.

Any help would be appreciated.  I am new to the linux world so please talk to me like a child that has been using windows for way too long!

---

### Post by tgalati4 on 2010-12-15
I found a similar eMachines on the curbside.  I installed Hardy server on it and it's been running for a couple of years.

---

### Post by dmelendez34 on 2010-12-15
Should I try and older version of Ubuntu then?  Older than 10.4?

---

### Post by sikander3786 on 2010-12-16
Welcome to the forums :-)

As the error message itself is suggesting,

> Then try booting with the 'noapic' option.

Did you try to boot with the noapic parameter? See here for details.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

If that doesn't succeed, try someother boot option from the same F6 menu. There are 6 of them and any of them might just work magically. You need to try them one-by-one.

---

### Post by dmelendez34 on 2010-12-17
Thank you for that link.  I had a keyboard with a busted f6 key.  I switched and was able to turn off acpi, noapic, nolapic, and nodmraid so it installed just fine...now my problem is when the computer rebooted after the install I got back the error I posted to begin this thread.  I am going to read more from the link you gave me...hopefully something there will tell me how to disable whatever is keeping the PC from loading ubuntu.  

BTW, I actually tried having the disc run and I pushed f6 and then I put an x next to acpi=off, noapic, nolapic, and nodmraid (just like I did when I ran the install)...unfortunately the error message still came up.

I will keep trying to get the system to boot off the hard drive now...baby steps. :)

---

### Post by sikander3786 on 2010-12-18
Press and hold down Shift key from your Bios screen until you see the grub menu. Highlighting the first entry in Grub menu, press 'e' to edit it. Navigate to the end of those lines using arrow keys and type 'noapic' at the end (without quotes). Press Ctrl + X to continue boot. Hopefully, it won't give any more error messages.

Once on the desktop, in order to make those Grub changes permanent, edit /etc/default/grub by,

Applications > Accessories > Terminal:
```
gksudo gedit /etc/default/grub
```

And type your parameters in between the quotes in this line.

```
GRUB_CMDLINE_LINUX=""
```

Run update-grub (You've to run this everytime you make any changes to Grub).

```
sudo update-grub
```

Reboot and see if that worked. Let us know about your progress.

---

### Post by dmelendez34 on 2010-12-18
Still no go on booting off hard drive.  I was able to hold shift add the command of 'noapic' (without the apostrophes) to the boot sequence that shows, but I still get the same error.  I tried also adding the 4 other options that I used when I got the CD to install ubuntu, one right under the other, but that did not work also.  

Could the memory be the problem?  Should I do the memory check?  I am guessing that is not the problem since I was able to do the full install that the memory is OK but I cant figure out why I cant at least boot up now that the OS is on the hard drive...?

---

### Post by dmelendez34 on 2010-12-18
tried booting in recovery mode with noapic but still got original error message...I noticed this time it also mentioned that it tried 3 different ways to get a timer to work but all 3 ways failed...can I turn off the timer(s) so I can boot?

---

### Post by dmelendez34 on 2010-12-18
OK so I finally got it to boot...I needed to put noapic after the word splash (2nd to last line) not after the last line showing on the edit grub screen.

I tried modifying the boot so I wouldn't have to type in "noapic" every time I boot but apparently I did something wrong....do I need to use the quotation marks or do I just type in noapic after the equal sign?  

I did the first command then I was asked for my password, then I typed in the second command that should have ended with noapic or "noapic" and then I typed in the third command and some script came up talking about a boot file and mem check and then it said done.

I rebooted but it did not modify the boot file because I had to type in noapic after the word splash again.

I am glad I am finally logged in!....now to figure out how to avoid having to type noapic every time I boot up the pc...I can see the light at the end of the tunnel. :)

---

### Post by sikander3786 on 2010-12-19
Did you run sudo update-grub after modifying the grub file?

Please post the output of this one.

```
cat /etc/default/grub
```

---

### Post by dmelendez34 on 2010-12-19
I will do the last command you posted but before I try again with the other steps, do I need to include the two " when I type noapic or do I exclude those marks?  

Should I capitalize noapic or leave it lowercase?

I will try again later on today and let you know how it went this time around.  Thanks for the help.

---

### Post by zerolatency on 2010-12-19
Oops, sorry cannot help.

---

### Post by dmelendez34 on 2010-12-20
Finally got it to boot without me having to use no apic command manually.  I got a popup box this time where I had to type in noapic in the quotation marks already included in that section of the file that opened.  

I ran update-grub command and I rebooted right after and everything is awesome now.  

Thank you for your help sikander.  I really appreciate it.  This forum is great for us newbies.  I already found a thread to help with my dvd playback/backup issues so I didn't have to add an additional thread.  

Hopefully one day I will be good enough on linux that I will be able to help others.

---


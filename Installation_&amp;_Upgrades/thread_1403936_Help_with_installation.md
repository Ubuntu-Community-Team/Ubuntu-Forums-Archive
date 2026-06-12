---
title: "Help with installation"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Scrub on 2010-02-10
I'm fairly new to the linux game, so please excuse my ignorance of linux workings.
 
I've recently revived and old computer, and have downloaded and burned the ISO to a CD. When I select the option of "Install Linux", some files load and text appears, etc.
 
After a bit (~5sec) the screen displays a pulsing ubuntu logo. Nothing else past that appears, so I have to press CRT-ALT-DEL to restart or shutdown the computer. Any help?

---

### Post by Bright_View on 2010-02-10
Could be many things.  What are the specs of this old computer that you have revived?  Are you sure all hardware is good?  Did you check the disk to make sure it burned with no errors?  etc.

---

### Post by Kir_B on 2010-02-10
Ditto on the disc check.

I had a similiar problem, but it was with the x86_64 cd version and so I had to fall back to the i386 version.

Also, can you boot the cd into demo mode?

---

### Post by ubudog on 2010-02-10
It does take a while to load.

---

### Post by Kir_B on 2010-02-10
Yeah it does. try to install from the icon on the desktop.

---

### Post by ubudog on 2010-02-10
How long did you wait before restarting the computer?

---

### Post by Kir_B on 2010-02-10
Sorry. Is this question directed to me? If so, please elaborate.

---

### Post by lidex on 2010-02-10
> **Scrub said:**
> I'm fairly new to the linux game, so please excuse my ignorance of linux workings.
 
I've recently revived and old computer, and have downloaded and burned the ISO to a CD. When I select the option of "Install Linux", some files load and text appears, etc.
 
After a bit (~5sec) the screen displays a pulsing ubuntu logo. Nothing else past that appears, so I have to press CRT-ALT-DEL to restart or shutdown the computer. Any help?

First of all, did you boot into a live-session - the option to use ubuntu without making any changes to your PC? If it can do that then it should run from a HDD install. Secondly, I'll reiterate the question posed by ubudog: how long did it hang at the logo before you rebooted? You may need to let it do it's thing for a longer period.

---

### Post by Kir_B on 2010-02-10
I think we waited between 3 and 5 minutes. If it hasn't booted up at the 5 minute mark, reboot. Which version are you using? The x86_64 or the i386?
                                          Peace. Kir_b

---

### Post by Scrub on 2010-02-11
I just used the download button on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). I don't know what version that was. The hardware for this computer is also fine.*

From the options menu, I simply chose install Ubuntu (not sure of the exact wording, have to check later.)

And with me not being a very patient guy, I waited max 45 sec before concluding that something wasn't working correctly and terminating the program

I've aalso seen something about a windows installer. Will downloading that and running it do the job of installing ubuntu as the second OS? Thanks for the help! *

---

### Post by Kir_B on 2010-02-11
> **Scrub said:**
> I just used the download button on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). I don't know what version that was. The hardware for this computer is also fine.*

From the options menu, I simply chose install Ubuntu (not sure of the exact wording, have to check later.)

And with me not being a very patient guy, I waited max 45 sec before concluding that something wasn't working correctly and terminating the program

I've aalso seen something about a windows installer. Will downloading that and running it do the job of installing ubuntu as the second OS? Thanks for the help! *

Windows will not help you with anything to do with linux. Try downloading via a torrent from "[COLOR=#cc33cc][Distrowatch]("http://distrowatch.com/table.php?distribution=ubuntu")[/COLOR]" and grab the i386, unless you're running a 64 bit system, which might require the X86_64 version{I have 64 bit system, but it doesn't work for me at all, so it might not work for others with 64bit systems}. If you're having problems accessing the demo mode {I prefer to install from Ubuntu's desktop}, try pressing the F4 key on your keyboard and select "safe graphics mode" and then "try Ubuntu without any change to your computer".
                            I hope this helps you Kir_b

P.S. I'll have a quick look for a link to Ubuntu's HTTP downloads.

---

### Post by Kir_B on 2010-02-11
If you need the 64bit download, just go to Ubuntu's website and click on "Alternative download options, including Ubuntu installer for Windows", which will provide more options. Stay away from the alternate installation cd's. If you intend to install Ubuntu via wubi in your Windows operating system, while running Ubuntu try to avoid altering it too much {mostly, just stay away from anything that says "grub", "Linux-headers" and "Kernel"} and avoid like the plague anything that suggests that it "upgrades" the system.

---

### Post by Scrub on 2010-02-11
> **Kir_B said:**
> If you need the 64bit download, just go to Ubuntu's website and click on "Alternative download options, including Ubuntu installer for Windows", which will provide more options. Stay away from the alternate installation cd's. If you intend to install Ubuntu via wubi in your Windows operating system, while running Ubuntu try to avoid altering it too much {mostly, just stay away from anything that says "grub", "Linux-headers" and "Kernel"} and avoid like the plague anything that suggests that it "upgrades" the system.
 
 
Thanks

---

### Post by ubudog on 2010-02-12
> **Scrub said:**
> Thanks

64bit has a lot of problems on all the computers I've tested it on.

---

### Post by recluce on 2010-02-12
> **ubudog said:**
> 64bit has a lot of problems on all the computers I've tested it on.

Such as? I have not encountered any 64-bit specific problems for quite a while.

---

### Post by recluce on 2010-02-12
I don't think we have enough information to analyze the problem. Before investing any more time:

To the OP:

boot your Ubuntu disk and from the initial menu, select "Check disk for defects". This will take quite a bit of time (about 5 minutes). Don't get impatient, go for a cup of coffee. 

If (**and only if**) the disk checks out error-free, restart and this time select "Try Ubuntu without any changes to my computer". Loading Ubuntu from CD will take time, at least 2 to 3 minutes, longer on marginal CD burns. Again, have a coffee, sit back, relax. Let us know if the live session works for you.

32bit or 64bit version does not matter much at this point. If you try to use the 64bit version on a CPU that does not support it, you will get a message "wrong architecture" (or something like this) very early on during the boot. In this case, you would have to download and burn a 32bit version. 

Using the 32bit version on a 64bit-capable system will limit the total amount of memory space to 4 GB. Depending on other factors, you probably will see a maximum of 3.5 to 3.8GB of RAM. If you have less than 4 GB RAM and do not plan to install more in this machine, there is no reason for the 64bit version.

---

### Post by Scrub on 2010-02-12
The disk checks out well, so I guess now all I have to do is wait for it to load. Will reply back with results.

---


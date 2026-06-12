---
title: "Is there a generic HOW TO INSTALL A PRINTER?"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by liddlem on 2010-12-14
I have tried various Linux distro's over the past 10 (or so) years and finally think it might be time to consider Linux as an option.  I have just installed Ubuntu 10.10 and am now trying to install a printer.
Now I suspect that you will want to know what printer I am trying to install?

Actually, I really want to know if there is (for an absolute newbie to Linux/Ubuntu) a plane and simple, STEP-BY-STEP (in english - not Linux speak) on "HOW TO INSTALL A PRINTER - any @#$%^&* printer"?   (Or any device for that matter?)

I have downloaded the relevant tar.gz file.
I have even managed to unzip it. (to cnijfilter-source-3.40-1 inside my Downloads folder)
But how do I get installed?

I have tried searching for HOURS and keep getting half baked answers where people assume that I have the slightest idea what I am doing.
for example, I have tried these
[http://www.ubuntux.org/forums/ubuntu-linux/installation](http://www.ubuntux.org/forums/ubuntu-linux/installation)
[http://support-au.canon.com.au/contents/AU/EN/0100237502.html](http://support-au.canon.com.au/contents/AU/EN/0100237502.html) (absolutely useless as a "how to" resource - canon is more interested about you agreeing to their license and if you're likely to purchase their product again. [I doubt it.])
[http://forums.overclockers.co.uk/showthread.php?p=15977303](http://forums.overclockers.co.uk/showthread.php?p=15977303)

Then I came across these links
[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)
Step 2 says
QUOTE
-----
  # 2: Build and install software

  Generally you need to type 3 commands as follows for building and compiling software:
  # ./configure
  # make
  # make install

  Where,
    * ./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
    * make will compile all the source files into executable binaries.
    * Finally, make install will install the binaries and any supporting files into the appropriate locations.
-------
UNQUOTE

The problem here is that it assumes I have a folder called ./configure and (presumably) a file called "install" that i can 'make?'
Inside the cnijfilter-source-3.40-1 folder there is a file called "makefile", but if I try to 'make makefile' I get a "No rule to target 'makefile'. Stop." error (What does this mean?)
...and nothing happens when I simply type "make" and press enter? so what's its purpose in this case?

then [http://forums.opensuse.org/english/get-help-here/64-bit/429014-canon-ip4760-64-bit-driver.html#post2107941](http://forums.opensuse.org/english/get-help-here/64-bit/429014-canon-ip4760-64-bit-driver.html#post2107941)
suggested
QUOTE
-----
The Canon rpms place the filter in /usr/lib/cups/filter and you need them in /usr/lib64/cups/filter
-----
UNQUOTE
but I cant paste the filter into the /usr/lib64/cups/filter folder cos the paste option is blanked out.


It would be REALLY nice to have some kind of generic HOW TO that steps a newbie through from absolute beginning to absolute end of process.

eg
1. Download the driver
2. untar/unzip/unpack the download as follows.
  a. Open the terminal - Click "Applications/Accessories/Terminal"
  b. Type "blah blah blah" into the terminal window
  c. Brief description of exactly what "blah blah blah" means

I desperately want to move away from Microsoft, (and i would like to the convert the school where I work) but If Linux/Ubuntu is always going to be as complex as this experience, it is unlikely that I will EVER get there. I simply do NOT have the time to go through the learning curve.
EVERYTHING still seems to be in cryptic mode. I am a 1 man show trying to manage 300 users.

PS - Trying o install a canon MP270 - but the downloaded driver pack appear to have source code for MP280 only. (I think there is NOT too much difference?)

sorry if I seem aggressive - I'm just highly frustrated.
Thanks for your input.

---

### Post by akand074 on 2010-12-14
Are you just printing? Or do you want the scanner to work too? For just printing all you have to do is plug it in via USB. The drivers are already built into the Linux Kernel. For scanning you do have to set it up, I can't recall off the top of my head how to do that, but I remember when I tried about a year ago I had trouble.

---

### Post by liddlem on 2010-12-14
thanks akand074.
Unfortunately the printer is complaining about missing drivers when I try to print. However, I would ultimately like to have the scanner working too, so a good HOW TO for all newbies would help..

---

### Post by ndefontenay on 2010-12-14
I've configured a network printer at my office on ubuntu just 2 days ago. I thought I was going into a rocky ride but it turned out to be really smooth (Once I found out the printer had been detected and available as an option already and I didn't have to look for it!)

Go to System>Administration>Printing. You should be able to handle there. It just takes the time to learn the new menu and read what it says (I was going too fast).

Nico

---

### Post by liddlem on 2010-12-15
I don't believe it, but I guess that the simple answer is "No"? (IE There is no simple way to install anything on Linux/Ubuntu)?

---

### Post by ezsit on 2010-12-15
You have downloaded the file from Canon ([http://support-au.canon.com.au/contents/AU/EN/0100237502.html](http://support-au.canon.com.au/contents/AU/EN/0100237502.html)) and extracted it to your desktop? Inside the folder that was created during the extraction you have a **install.sh** file and a folder titled **packages**. I would open a terminal in the same directory as the scangearmp-mp270series-1.40-1-i386-deb directory and type:

**sudo ./install.sh** 

This should run the install script. If the script does not execute properly, I would copy both .deb files from the packages folder into the same folder with the install.sh file and try again. It should install itself and after a reboot, CUPS should see the new drivers available.

If the install script still does not work, you can browse to the directory containing the two deb files and right-click on one and select the option to install using Software Center (if you are using Ubuntu 10.10). If you do not have Ubuntu 10.10, therre should be an option to open the package with **Gdebi**. Gdebi is a program that allows you install individual deb packages. After installing both deb files, reboot and CUPS should see the new drivers available and allow you to add a printer with the Printer app in the System/Administration menu.

---

### Post by ezsit on 2010-12-16
To answer your question as to whether there is an easy way to install anything under Linux, the answer is typically YES - it just works. 

When you installed Ubuntu, did you need to locate drivers for your sound card, your video card, your network card, motherboard chipset drivers, or any other component? Probably not. Why? Because Ubuntu autodetected everything and set it up for you. If you needed or wanted proprietary video drivers then Ubuntu asked you if you wanted to install them and did it for you.

Ubuntu will autodetect hundreds of printers and set them up automatically as well. Your particular model is not supported because the manufacturer of the printer does not release their print drivers into the open source community. 

Canon makes some drivers available as a binary download only - this means that Linux distributions will not support your printer out of the box. This is not a fault of Linux or Ubuntu but a fault of the manufacturer. Buy most any HP, Epson, or Brother printer and your printer will get automatically setup for you.

If people do some research on Linux compatible and friendly hardware and buy from Linux friendly manufacturers, then these problems would not happen. 

If you bought a Mac, it would be your responsibility to buy Mac compatible hardware and software. If you bought a Mac and then bought a printer without first checking to see whether that printer were Mac compatible, would you then turn around and blame Apple for not supporting your printer? Sounds ridiculous, no? What should happen is that the buyer in this scenario should contact the printer manufacturer and complain that the printer should come with Mac support. It is the same with Linux, if more people complained to the hardware manufacturers about lack of Linux support, the situation might get better.

---

### Post by BicyclerBoy on 2010-12-17
In all fairness to Canon, the Linux install help info is very good.
In your downloaded files you will find a step by step install guide.
They have provided the (some) source code & 32 bit pre-compiled binaries (debs).

I have the same printer..The 32 bit drivers work well; printer & scanner.
The driver GUI even looks like Linux GUI should.
You will need to know how to force 32 bit driver on 64 bit platform.

I found my compiled 64 bit install would disappear after reboots/upgrades & so reverted to the 32 bit pre-compiled. This was most likely my fault.

---


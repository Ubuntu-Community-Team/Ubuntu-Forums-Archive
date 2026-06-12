---
title: "Need help with Ubuntu install on IBM thinkserver"
date: 2016-02-04
forum: Installation &amp; Upgrades
---

### Post by JoGotta on 2016-02-04
I got a new server and monitor yesterday... I am launching a small business from my home and time is pretty critical at this juncture.

I installed Fedora 23 only to find out that it doesn't support my new monitor and even if I can get a driver for the monitor I won't be able to build the kernel myself to add it because it's Fedora.  (WOW has Linux changed since the last time I installed it at home!)

I'm not new to Linux but it has been 15 years since I built a kernel and coped with hardware issues.

I've read a lot about Ubuntu and am excited to try it out but I need some help getting the Fedora installation off the hard drive so it will boot from the ISO on a thumb drive.  

Next if someone can take a look at my system and tell me if there are any absolute deal breakers that would be great.

[COLOR=#111111][FONT=Arial]Lenovo ThinkServer TS140 70A4000HUX i3-4130 3.4GHz 16GB 3TB 7200rpm HDD Server Desktop Computer
[/FONT][/COLOR][TABLE="class: a-keyvalue prodDetTable, width: 768"]
[TR]
[TH="class: a-color-secondary a-size-base prodDetSectionEntry, bgcolor: #F3F3F3"]Processor[/TH]
[TD="class: a-size-base"]3.4 GHz Intel Core i3[/TD]
[/TR]
[TR]
[TH="class: a-color-secondary a-size-base prodDetSectionEntry, bgcolor: #F3F3F3"]RAM[/TH]
[TD="class: a-size-base"]16 GB[/TD]
[/TR]
[TR]
[TH="class: a-color-secondary a-size-base prodDetSectionEntry, bgcolor: #F3F3F3"]Hard Drive[/TH]
[TD="class: a-size-base"]3000 GB[/TD]
[/TR]
[TR]
[TH="class: a-color-secondary a-size-base prodDetSectionEntry, bgcolor: #F3F3F3"]Graphics Coprocessor[/TH]
[TD="class: a-size-base"]Intel HD Graphics 4400[/TD]
[/TR]
[TR]
[TH="class: a-color-secondary a-size-base prodDetSectionEntry, bgcolor: #F3F3F3"]Card Description[/TH]
[TD="class: a-size-base"]Intel HD Graphics 4400[/TD]
[/TR]
[TR]
[TH="class: a-color-secondary a-size-base prodDetSectionEntry, bgcolor: #F3F3F3"]Graphics Card Ram Size[/TH]
[TD="class: a-size-base"]1.7 GB[/TD]
[/TR]
[TR]
[TH="class: a-color-secondary a-size-base prodDetSectionEntry, bgcolor: #F3F3F3"]Number of USB 2.0 Ports[/TH]
[TD="class: a-size-base"]2[/TD]
[/TR]
[TR]
[TH="class: a-color-secondary a-size-base prodDetSectionEntry, bgcolor: #F3F3F3"]Number of USB 3.0 Ports[/TH]
[TD="class: a-size-base"]6[/TD]
[/TR]
[/TABLE]
[h=1]ASUS VE278H 27" Full HD 1920x1080 2ms HDMI VGA Back-lit LED Monitor[/h]

---

### Post by oldos2er on 2016-02-04
Moved to Fedora/Redhat.

You might be better off asking in [http://fedoraforum.org/](http://fedoraforum.org/)

---

### Post by JoGotta on 2016-02-04
LOL, wow, really?  I don't think you read my entire post but moved this based on the title.. I just want to format it safely so I can get Ubuntu installed and if I got anything at all from the fedora site after waiting a day and a half I wouldn't be looking to switch to ubuntu.

Maybe going with Linux is a really really bad idea

---

### Post by oldos2er on 2016-02-04
> **JoGotta said:**
> LOL, wow, really?  I don't think you read my entire post but moved this based on the title.. I just want to format it safely so I can get Ubuntu installed and if I got anything at all from the fedora site after waiting a day and a half I wouldn't be looking to switch to ubuntu.

You're right, I apologize. I changed your thread title a bit in addition to moving your thread to Installation & Upgrades.

Are you wanting to install Ubuntu Server, or the desktop version?

---

### Post by howefield on 2016-02-04
So the monitor worked fine whilst you installed the system ?

Sounds more likely that the video adapter is the problem.

---

### Post by JoGotta on 2016-02-04
The monitor works fine with command line.. when I try to start x windows it goes blinky

Understood.. THANK YOU.. and the server .. not desktop.

but I don't want to fix the Fedora install.. I want to do Ubuntu.. I just need to know how to get Fedora off safely so I can install Ubuntu server

---

### Post by howefield on 2016-02-04
Was it the server edition of Fedora that you installed ? If so, there is no GUI unless you have manually installed one, you'll find the same with Ubuntu server edition.

Why on earth would a server have a graphical user interface. Nothing stopping you installing one, however unusual that may be.

---

### Post by JoGotta on 2016-02-04
I've wasted too much time on this.. I just did rm -fR *

It rendered my shell unusable .. burning the ubuntu to thumb drive now.. wish me luck lol

---

### Post by howefield on 2016-02-04
Luck is probably the least of your worries, but... good luck anyway :)

---

### Post by JoGotta on 2016-02-04
OK, so that was a bad idea.. I have a lot of development work that needs to get done.. now it's stuck at grub.. I can't get past grub.. I can't get it to just boot from the damn thumb drive.. grrrr

Ubuntu is installing lol  I'll be back if I run into graphic issues.. THANKS

Absolutely no issues running the GUI, posting this from my Ubuntu install..

Now if I could just figure out how to get desktop icons instead of that bar on the side.. and where is the terminal window .. I'd be all set for quite some time LOL

---

### Post by CharlesA on 2016-02-04
Hit the windows key and do a search for Terminal. Assuming you installed from the Ubuntu Desktop iso.

Out of curiosity, what type of business are you trying to start?

Do you have a contingency plan in the event the server goes down?

---

### Post by yancek on 2016-02-04
Other ways to open a terminal are to simultaneously hold down the Ctrl+Alt+t keys which will open it.
Go to the Dash, the Ubuntu logo in the extreme upper left and click it and in the search box type terminal, then click the terminal icon below.
Not sure how you would move the panel on the left but I know it can be done.  You can create a desktop shortcut from a terminal with this command:

gnome-desktop-item-edit /home/don/Desktop --create-new

Opens a window, fill in the boxes.  It probably isn't installed by default and if not, it will prompt you to install and give the command:

sudo apt-get install --no-install-recommends gnome-panel 

I'm sure there are other ways.

---

### Post by buzzingrobot on 2016-02-05
You can build your own kernel on Fedora:[ ]("https://fedoraproject.org/wiki/Building_a_custom_kernel")[https://fedoraproject.org/wiki/Building_a_custom_kernel](https://fedoraproject.org/wiki/Building_a_custom_kernel)

Fedora supports **two **releases at any given time. Given Fedora's purpose in life, some users might want to stay with the older of the two releases.  That's Fedora 22 currently. (And still "newer" than many common Linux distributions.)  After Fedora 24 is released in May, F22 will be EOL'd, so upgrade in place to F23, and so on throughout future release cycles.

Fedora publishes a list of "Common Bugs" for each release that are not considered serious enough (or perhaps fixable) to delay a release: [https://fedoraproject.org/wiki/Common_F23_bugs](https://fedoraproject.org/wiki/Common_F23_bugs)

---


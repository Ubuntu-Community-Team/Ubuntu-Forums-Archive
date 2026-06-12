---
title: "How to Reinstall Ubuntu 12.10"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by fosbinder on 2013-04-03
Dont you love all these nub questions awesome Ubuntu Community?

---

### Post by slickymaster on 2013-04-03
Here is a great tutorial on how to do it: [How to reinstall Ubuntu easily]("https://sites.google.com/site/easylinuxtipsproject/reinstallation")

---

### Post by fosbinder on 2013-04-03
Thank you so much for the quick response

---

### Post by matt_symes on 2013-04-03
Hi

> **fosbinder said:**
> Dont you love all these nub questions awesome Ubuntu Community?

One thing about the Ubuntu Forums is that we don't mind answering the same questions over and over again.

We understand that for many, Ubuntu is the first Linux distribution they try.

We must all start somewhere and Linux can be a big change if your used to Windows.

Personally i think that the regular forum members and posters are some of the best in the world for the effort they put in.

Kind regards

---

### Post by fosbinder on 2013-04-03
you mind stickin with me thru the reinstall?

---

### Post by matt_symes on 2013-04-03
Hi

> **fosbinder said:**
> you mind stickin with me thru the reinstall?

Post back any problems or questions you have about the install.

Even if i am not here (it's getting late here), there are many users that will be.

Kind regards

---

### Post by fosbinder on 2013-04-03
I dont have G-Parted...Nvm Found it LOL XD

---

### Post by slickymaster on 2013-04-03
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Follow these [instructions]("https://help.ubuntu.com/community/BurningIsoHowto") to burn the .ISO image to CD

---

### Post by fosbinder on 2013-04-03
im having issued with step 2 [here]("https://sites.google.com/site/easylinuxtipsproject/reinstallation").. I clicked swap off on linux-swap then delete it and then delete extended /dev/sda2 and swap dissapears then extendened becomes unalocated and at the end ext4 /sda1 cannot be deleted.. and the unmount option results in an error

---

### Post by fosbinder on 2013-04-03
restarting process

---

### Post by fosbinder on 2013-04-03
I cant get the terminal up when booting from the disk to download Gparted.. any ideas?

---

### Post by pfeiffep on 2013-04-03
Do you have an install CD / DVD (sometimes called live)  that you made? If so boot it from your dvd - gparted is probably installed on the install CD ... you should be able to continue from there. Is this the step 2 to which you referred?
> [COLOR=#000000][FONT=Arial]2. Boot your computer from the Ubuntu DVD and start GParted: [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Click on the grey Ubuntu logo in the top of the side panel (Dash home). Query: [/FONT][/COLOR][COLOR=#0000FF][FONT=Arial]Gparted[/FONT][/COLOR][COLOR=#000000][FONT=Arial]. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Click on Gparted Partition Editor.[/FONT][/COLOR]
If so it appears that you might have tried this from your installed 12.10.
Are you on the chat line?

---

### Post by fosbinder on 2013-04-03
I cant get Gparted loaded while booted from disk as instructed in the above mentioned tutorial... What should I do?

---

### Post by pfeiffep on 2013-04-03
So you opened dash and typed ```
gparted
``` ? correct. And it didn't load? any errors?
try ```
Alt-Ctrl-t
```  to open a terminal and type ```
gksudo gparted
```

---

### Post by fosbinder on 2013-04-03
i was trying to find it with the ubuntu search and couldnt find terminal  or gparted but the shortcuts and command worked =) Thank you

---

### Post by fosbinder on 2013-04-03
so I got there and now I cant deactivate swap on linux-swap... (-) Could not deactivate swap    swapoff:/dev/sda5:swapoff failed: Cannot allocate memory

Any Thoughts?

---

### Post by Bucky Ball on 2013-04-03
*Thread moved to **Installation & Upgrades**.*

---

### Post by fosbinder on 2013-04-03
Sry Bucky =) , any thoughts?

---

### Post by fosbinder on 2013-04-03
I love you all.. just wish you had more time and I had less lagg

---

### Post by fosbinder on 2013-04-03
Would a regular old reinstall without this step hurt my system?.. its just a fresh install of Ubuntu that I messed up atm..

---

### Post by agent-squirrel on 2013-04-03
A regular reinstall wont hurt but only if you are happy to loose the current Ubuntu install.

---

### Post by fosbinder on 2013-04-03
been sittin at this forum for 2 hours now.. time to take a break..

---

### Post by Bucky Ball on 2013-04-03
You might consider 12.04 LTS. It has five years support rather than eighteen months. All depends on how you use your machine, of course. I generally have the current LTS release as my main squeeze and a couple of partitions for playthings (interim releases and anything else that takes my fancy). Doesn't matter if I break these as always have 12.04 LTS to fall back on (supported until April 2017). ;)

---

### Post by fosbinder on 2013-04-03
wow.. something is wrong with my connection cause I refreshed this a billion times and didnt see your message.. thank you!

---

### Post by fosbinder on 2013-04-03
so I decided to reinstall without removing the partitions and now the installer cannot setup the swap.. what should I do?

The creation of swap space in partition #5 of SCSO1 (0,0,0) (sda) failed.

---

### Post by pfeiffep on 2013-04-04
If you don't have any files, pics, music on Ubuntu then you should proceed with an install similar to the original.

---


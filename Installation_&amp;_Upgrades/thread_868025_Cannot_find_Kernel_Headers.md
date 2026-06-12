---
title: "Cannot find Kernel Headers"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Antishatter on 2008-07-23
I am somewhat new to Ubuntu and I am currently trying to locate the kernel headers for the hardy 8.6.24.3 kernel. I have not been able to find this online despite several hours of searching and numerous attempts at using apt-get or apt-search. If someone could point me in teh correct direction I would be forever grateful. I was able to locate the kernel source but alas there was no trace of the headers. Thanks in advance! Also, sorry if this is a really dumb question I am still pretty new to the linux community.

---

### Post by Antishatter on 2008-07-23
> **Antishatter said:**
> I am somewhat new to Ubuntu and I am currently trying to locate the kernel headers for the hardy mid 2.6.24.3 kernel. I have not been able to find this online despite several hours of searching and numerous attempts at using apt-get or apt-search. If someone could point me in teh correct direction I would be forever grateful. I was able to locate the kernel source but alas there was no trace of the headers. Thanks in advance! Also, sorry if this is a really dumb question I am still pretty new to the linux community.

I fixed what was incorrect in my original post because I couldnt locate the edit button! I changed the version to Hardy mid 2.6.24.3. Thanks again!

---

### Post by coffeecat on 2008-07-23
> **Antishatter said:**
> I fixed what was incorrect in my original post

Whew! I thought for a minute that I'd been transported into a fairy tale and had awoken after a 500-year slumber. I believe the 8.6.24.3 kernel will include a stable driver for starship transportation devices and is going to be incorporated into the upcoming Ubuntu Krusading Klingon release. :wink:

Do you mean you can't find the kernel headers in the filesystem or in the Synaptic package manager? If the latter, they are listed under linux-headers*. And are you sure you mean 2.6.24.3? Have a look in Synaptic to see what I'm referring to.

**Edit:** by the way, the edit button is next to the quote button, bottom right of your post.

---

### Post by Antishatter on 2008-07-23
> **coffeecat said:**
> Whew! I thought for a minute that I'd been transported into a fairy tale and had awoken after a 500-year slumber. I believe the 8.6.24.3 kernel will include a stable driver for starship transportation devices and is going to be incorporated into the upcoming Ubuntu Krusading Klingon release. :wink:

Do you mean you can't find the kernel headers in the filesystem or in the Synaptic package manager? If the latter, they are listed under linux-headers*. And are you sure you mean 2.6.24.3? Have a look in Synaptic to see what I'm referring to.

**Edit:** by the way, the edit button is next to the quote button, bottom right of your post.
Ah it is there now but I honestly dont recall it being there because I specifically checked there because that is where it is located on every forum on the internet. 

I do in fact mean 2.6.24.3 and I know where they should be on my system but as they are not there I need to get a copy somewhere and I couldnt find them available for download anywhere. I even had a few linux gurus from around the office hunt for them and come up with nothing. I need them to install a video driver so I can get X running so I am currently just using the command line interface. I am not familiar with synaptic package manager so Im not sure if I can do that without a gui.

---

### Post by coffeecat on 2008-07-23
> **Antishatter said:**
> I am not familiar with synaptic package manager so Im not sure if I can do that without a gui.

I see your problem. You are quite right; you can only run Synaptic from a GUI.

I still think the kernel number is wrong. If your Linux gurus haven't suggested the following, first of all from the command line, do:

```
uname -r
``` to see which kernel you are running.

Then:

```
sudo apt-get install linux-headers
```Don't worry, it won't install anything. You have to be more explicit. It will simply list all the linux-headers* packages available in the repository, so you can select the one appropriate for your kernel.

What puzzles me is that I thought the kernel-headers came ready installed in a default install of Ubuntu, but I could be wrong.

**Edit:** If you've got a working internet connection, you might want to:

```
sudo apt-get update
```

first.

---

### Post by Antishatter on 2008-07-23
> **coffeecat said:**
> I see your problem. You are quite right; you can only run Synaptic from a GUI.

I still think the kernel number is wrong. If your Linux gurus haven't suggested the following, first of all from the command line, do:

```
uname -r
``` to see which kernel you are running.

Then:

```
sudo apt-get install linux-headers
```Don't worry, it won't install anything. You have to be more explicit. It will simply list all the linux-headers* packages available in the repository, so you can select the one appropriate for your kernel.

What puzzles me is that I thought the kernel-headers came ready installed in a default install of Ubuntu, but I could be wrong.

uname -r does return 2.6.24.3 and yes I checked it before I made the thread haha. This board is set up at my office and it is fairly difficult to get a computer out onto the internet unless it is the laptop they issue you, any chance I can pull the headers down on my windows laptop?

---

### Post by coffeecat on 2008-07-23
> **Antishatter said:**
> any chance I can pull the headers down on my windows laptop?

Theoretically, yes. If you can find the appopriate .deb package on an Ubuntu repository mirror (you can find a list somewhere on the Ubuntu website), you could download it, copy it to your Ubuntu installation and install it with dpkg.

But I'm still puzzled. Synaptic and apt-get are showing nothing less than 2.6.24-16.30, with the latest being 2.6.24-19.36. You haven't left out a '16' by any chance. And note the use of '-', not '.'. Also, if you do mean 2.6.24-16.30, that is 30 at the end, not 3. It's a release number, not a decimal number. Apologies if you know all this, but these are easy things for the Linux newcomer to trip up on.

Or did you install from an alpha or beta version of Hardy? I don't know what the kernel numbers in the pre-release versions were as I didn't bother playing with them, but it's the only other way I can explain that version number of yours.

---

### Post by Antishatter on 2008-07-23
The exact distribution I have can be found here

[http://cdimage.ubuntu.com/mobile/releases/hardy/ume-8.04-menlow.mic.tar.bz2](http://cdimage.ubuntu.com/mobile/releases/hardy/ume-8.04-menlow.mic.tar.bz2)

But yeah the kernel it comes with is definitely 2.6.24.3.

---


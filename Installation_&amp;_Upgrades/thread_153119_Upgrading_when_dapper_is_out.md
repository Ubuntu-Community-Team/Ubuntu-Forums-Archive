---
title: "Upgrading when dapper is out?"
date: 2006-03-31
forum: Installation &amp; Upgrades
---

### Post by ELD on 2006-03-31
Sorry if i got name wrong i think its dapper?

Back to the point --> when the next version is out do i have to do a fresh install over breezy or can i simply upgrade?

---

### Post by arctic on 2006-03-31
You can upgrade. Change the mirrors from breezy to dapper, then log into a safe terminal session (not a gui) and run
apt-get update
apt-get upgrade
apt-get dist-upgrade
then reboot.

---

### Post by gnu2tux on 2006-03-31
The next version is called Ubuntu 6.07 (Dapper Drake) and will be out in June/July.

You can upgrade at any time you like by simply editing (as root) the file /etc/apt/sources.list and searching and replacing for all occurances of the word 'breezy' with 'dapper'.

Then simply do 

$sudo apt-get update && apt-get upgrade && apt-get dist-upgrade

That's you. I'm running dapper now and it's great.

Al.

---

### Post by ELD on 2006-03-31
Excellent, couldn't of asked for better answers, thank you to both of you!

---

### Post by Sef on 2006-04-02
> he next version is called Ubuntu 6.07 (Dapper Drake) and will be out in June/July.

Dapper will be out 1 June.

---

### Post by ELD on 2006-05-02
Sorry to bring it up again.

When upgrading will my nvidia drivers still work?

---

### Post by gnu2tux on 2006-05-02
Hi,

  You will need to upgrade the restricted kernel drivers when you upgrade the kernel.

You can do this simply by typing the following at the command prompt:
```

$ sudo apt-get install linux-restricted-modules-`uname -r`

```

Cheers!

Al

---

### Post by ELD on 2006-05-16
Sorry to bring this topic up again but, what would happen if upgrading broke things, would i a novice linux user be able to fix them?

Would games i have installed still work?

---

### Post by gnu2tux on 2006-05-16
I've upgraded my distro through from warty warthog (the first one), and it's always been fine. Sure, there were little hickups here and there, but most things were fairly straight forward and if you get stuck you can always ask here!

the gotchas that you should know-

if you use a special driver for your video card such as nv, then be aware you will need to download the linux-restricted-modules driver for the new kernel (for nvidia kernels), or if you are using ati, refer to the installation guide for ati cards at the ubuntu wiki.

some non ubuntu software broke - eg: skype broke. I have skype running now, but that's only because I downloaded the redhat version and converted the rpm into a deb. Annoying, but skype don't build binaries for ubuntu, so it's no fault of ubuntus.

There were other things, but as you can see, all fairly trivial.

Good luck!

Al.

---

### Post by glenn45 on 2006-05-19
what if i dont have internet access and need to upgrade using distro cd? do i have to reinstall all ? or is there a better way of doing the upgrade?

---

### Post by Buffalo Soldier on 2006-05-19
Something for you to remember... doesn't matter which method of upgrade, it's best to backup all your data first.

---

### Post by Magiczero on 2006-05-26
Hellol

If I get the upgrade from the terminal how big is the download because my ISP is gay and they give me limited download space to 10 gigs a mounth.  I NEED to know how big the download is before I can download the upgrade so my ISP doesnt max out my download space!  Is it better just for me to get the CD or have somebody else download it when it comes out?  Thanks

---

### Post by gnu2tux on 2006-05-26
If you wait off until dapper is finally released next month I would imagine that the download will be in the region of 500-600 mb.

but seriously dude, you need to get a less homosexual isp.

:)

---

### Post by Magiczero on 2006-05-26
I wish I could get a better isp but I live in the middle of nowhere and im on satilite internet because where I live the lines are to old to get dsl around here.  It costs like $40 more to get unlimited download space and my dad doesn't wana pay for unlimited and I keep telling him we need to and he says no.  Thanks for all the help!

---


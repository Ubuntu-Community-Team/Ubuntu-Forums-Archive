---
title: "Failed Upgrade- No GUI"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by skeetwood-mac on 2010-05-11
So for some reason I tried to upgrade even though I've heard a lot how that never works. For some reason I thought I'd give it a try. Well I got a million error messages and then it said it failed. But then it kept going and said it finished. Everything  was working then my computer just froze up and I had to reboot. Now when its booting it says no acer-wmi interface and then gives me a command line login. And it tells me I have the new version loaded but its just all just text. I can login and have a working command line but when I try startx a bunch of text flashes quickly and theres something about an error but it goes so fast I can't read it. And then it just goes to a black screen where nothing happens. Im pretty dissapointed because I was just getting used to ubuntu and was starting to like it but now my computer is completely useless. I hope someone can help.

Thanks in advance.

---

### Post by Catharsis on 2010-05-11
Try:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get dist-upgrade
```

It'd also be nice to know your graphics card:
```
lspci | grep VGA
```

---

### Post by skeetwood-mac on 2010-05-11
> **Catharsis said:**
> Try:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get dist-upgrade
```

It'd also be nice to know your graphics card:
```
lspci | grep VGA
```

I tried update and -f install before and update would work but -f install would just give me a bunch of errors. So I did clean this time first and tried again and it installed open office and libmagickcore and then I did --configure -a and dist upgrade and it downloaded and installed a whole  bunch more things and then I thought it might be complete so I typed startx but it just went to a blank screen so I had to reboot and it still says "No or unsupported acer wmi interface and then it flashes the ubuntu flash screen but this time there is the ubuntu logo for a second and then it goes blank and does nothing. No command line or anything. Is there anything else I can do now or is it just completely broken?

---

### Post by Catharsis on 2010-05-11
What graphics card do you have?

---

### Post by skeetwood-mac on 2010-05-11
> **Catharsis said:**
> What graphics card do you have?

Not sure I can't check now becuase theres no command line or anything.

---

### Post by skeetwood-mac on 2010-05-13
So my computer is useless now. Is there any way of fixing it? I'd at least like to be able to get some of my stuff off the hard drive before I have to reinstall the OS again. Any ideas?

---

### Post by skeetwood-mac on 2010-05-13
so I booted into ubuntu with a live cd I got from a friend. And it says that my hard disk has many bad sectors. Im hoping thats just because it has a bad install of ubuntu.

---

### Post by skeetwood-mac on 2010-05-15
any other options before I just have to reinstall the os?

---

### Post by skeetwood-mac on 2010-05-19
alright so I heard that the newlinux kernel willnot work on my acer travel mate 370 because of the video card. So is there anyway I can down-grade or something? I can boot into ubuntu with the live cd which is how Im writing this. But I have no wireless. I'd like to be able to save my files from the old install. Any possibilities or should I just wipe everything off and reinstall?

---


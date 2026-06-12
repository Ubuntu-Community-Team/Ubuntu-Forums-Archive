---
title: "Update Manager Hung - Spinning Globe"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by BlastXng on 2012-02-28
Hello Folks

I was notified that I had a software update with my Kubuntu 11.10. Previously when I went to Update Manager I got an "Authenticatin Error" (Exact=This operation cannot continue since proper authorization was not provided)  and read about how to possibly correct it here:
[http://ubuntuforums.org/showthread.php?t=1891806&page=2](http://ubuntuforums.org/showthread.php?t=1891806&page=2)

I did the following:
sudo apt-get purge policykit-1 policykit-desktop-privileges polkit-kde-1

followed up 

sudo apt-get install policykit-1 policykit-desktop-privileges polkit-kde-1

Once this completed I then went into Update Manager. 

I then clicked on it, told it to go check for any updated and at that point "Update Manager" hung.. When I put my mouse over the program the arrow changes to a spinning globe.. 

My set-up is a AMD Phenom II Black Quad-Core, 16GB RAM & 500GB HD on ASUS MB. 

Any thoughts on what might be causing this? I'll be more than happy to post information that could help. :confused:

Thanks

---

### Post by LinuxFan999 on 2012-02-28
Here is an alternative way to update:

Go into the terminal then type these:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by BlastXng on 2012-03-01
> **LinuxFan999 said:**
> Here is an alternative way to update:

Go into the terminal then type these:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Appreciate these commands, however I already use these when I am in a pinch. But somethimes I don't want to install all of the items that the software manager might show like an updated Thunderbird or Firefox that would break my existing installation. 

Any other thoughts of what info I might need to grab to post?

---


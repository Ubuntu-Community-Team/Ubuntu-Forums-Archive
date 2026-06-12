---
title: "Issue while Downloading"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by LinXNut on 2011-04-22
Hi, I was trying to download wine through the terminal with "sudo apt-get install wine." Everything was going find until I forgot my laptop was dead, and the power cord came out, so it died. I rebooted my computer, and now I cannot do anything with the package manager, or even really run "apt-get." Is there a way I can refresh or fix this error?

Here is the output I get:

```
jonathan@Xubuntu-Lap:~/Desktop$ sudo apt-get install
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jonathan@Xubuntu-Lap:~/Desktop$
```


Thanks!

---

### Post by mörgæs on 2011-04-23
What happens if you boot the machine again and run 

```
sudo apt-get clean
```?

---

### Post by varunendra on 2011-04-23
Well.. if you really can't use even 'apt-get', try booting in recovery mode and try the '**dpkg - repair broken packages**' option.
You may have to manually delete packages from /var/cache/apt/archives directory as well as 'partial' directory in it.

If it does not work, you may try to boot from a live cd and try fsck on your filesystem.

---


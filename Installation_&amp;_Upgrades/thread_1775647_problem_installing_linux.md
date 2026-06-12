---
title: "problem installing linux"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by Rrotem on 2011-06-05
Hi guys
 
I need your help, I'm newbe to linux.
I have an old computer that had linux installed on it. I don't know which and I don't know the user name or password.
I've downloded the new version of "ubuntu", burned it on a disk (from a differnt computer) and tried to install it.
I got an error message:
general error mounting filesystem
a maintence shell will now started
contorol-D will terminate this shell and reebot the system
 
I looked it up on the internet, they said I need to edit files.
I can't and I don't wat to, I just want a fresh installation.
 
Can you help me?
Tanks

---

### Post by raja.genupula on 2011-06-05
if you want to do a fresh install then connect that hard disk to to another system and erase all the data and then do reinstall

---

### Post by kansasnoob on 2011-06-05
When you first boot the live CD, right after the system/BIOS screen passes you'll see a purple screen with two small graphics at the bottom. At that moment you have about 3 seconds to press a key.

Then the language screen will appear followed by a screen with boot options. Choose "check disc for errors", it'll take a few minutes to run.

If it shows any errors then you have a bad burn, or possibly a bad download so look here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If it says "no errors" found then select "try Ubuntu w/o changes" and from the Live desktop post some general system info, like the output of:

```
sudo lshw
```

A simple way to do that is to run:

```
sudo lshw > hardwareprofile.txt
```

You'll then find a file in the home folder titled "hardwareprofile.txt" and you can either compress and attach it here using the paper-clip thingy or copy-n-paste the output into code tags using the #.

---

### Post by Rrotem on 2011-06-05
tanks, it worked

---

### Post by Rrotem on 2011-06-05
I have a new problem :(
 
The installation went well, I restart the computer and it's stuck on "checking battry state".
 
I've tried reinstalling - same thing.
 
Please help, tanks

---


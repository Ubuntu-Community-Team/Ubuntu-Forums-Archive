---
title: "Python broken on upgrade to 18.10"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by raccoonstrait on 2018-10-19
Good day all,

I ran dist-upgrade this morning and there were a couple of issues I wanted to point out.

First, during the upgrade unpack/install/setup phase there were numerous errors noted with regard to gdkpixbuf not being able to find its cache. In the end however this did not appear to be an issue.

Upon reboot, I got a very dark screen, so dark I could barely make out anything on the desktop and could not see the cursor at all. I had to use power off to do anything more. After two attempts, I then ran recovery mode from the grub menu. DPKG reported that a python symlink was broken. So I dropped to the root mode console and ran

```

sudo aptitude install python

```

which requested to delete one more package, but also appears to have fixed the symlink problem.

I will mark this issue as solved, I just wanted the community to know about the issues and a fix. Whether it is the right fix, I don't know, but it worked.

Raccoon Strait

---

### Post by roma.parabellum on 2018-10-19
Hi!
It looks like I have faced the similar issue. At start I just see pure black screen but with cursor (in form of underscore) at top left corner. During booting in recovery mode, as I select reparing packages option I got the same message about python, but when I select at this stage - "continue to normal booting" - it get me to normal loading of ubuntu.
Unfortunately I failed to use your advice - terminal returns "sudo: aptitude: command not found".
Could you please help?

---

### Post by #&amp;thj^% on 2018-10-19
Try:
```
sudo apt install aptitude
```
Then run again:
```
sudo aptitude install python
```

---

### Post by roma.parabellum on 2018-10-19
Thanks! The python problem is resolved but booting still does not work properly - just black screen with blinking cursor. But sequence: 1. boot in recovery mode -> 2. option  "continue to normal booting" (without any action in between) works well... What is wrong? ( And may be it might matter - at the very beginning of booting I see a lot of logs moving through the screen from top to botton. It did not work this way at 18.04...

---

### Post by #&amp;thj^% on 2018-10-19
upgrading can be a very confusing ordeal, for both you and your system. ;)
I think you would have had a better experience with a clean install. (Less cruft left behind)

---

### Post by raccoonstrait on 2018-10-19
While doing a clean install makes sense for some, for others it is a pain to get back to where you were. Even if one has a copy of get-selections

```

dpkg --get-selections > /Your Saving Place/Package.list

```

and know the proper sequence to install those packages

```

#dpkg --get-selections > /media/Your Saving Place/Package.list


sudo cp /Your Saving Place/Package.list /home/Your/Desktop/
sudo apt-get update
sudo apt-get install dselect
sudo dselect update
apt-cache dumpavail > ~/temp_avail
sudo dpkg --merge-avail ~/temp_avail
rm ~/temp_avail
sudo dpkg --set-selections < /home/Your/Desktop/Package.list
sudo apt-get dselect-upgrade -y


sudo rm /home/Your/Desktop/Package.list


#special to my machine but might be valuable to to other, change system76 to your appropriate system or ignore
#http://docs.system76.com/articles/restore


sudo add-apt-repository "deb http://archive.canonical.com/ubuntu $(lsb_release -sc) partner"
sudo apt-add-repository -ys ppa:system76-dev/stable
sudo apt update


sudo apt-get install -y system76-driver
sudo apt-get install -y nvidia-346

```

It will still install stuff that may not be actually needed. I have installed things, and then found they didn't help but then neglected to uninstall them. They would be included in such a process.

I would love to see an aptitude or apt process that selected unused programs for deinstallation but in a GUI so that one could choose which apps are deinstalled and no requirements were hurt. Sometimes an unused installed app is because I might want to use it someday. In other instances I installed an app to try to fix an issue, which didn't help, but then should be removed because it hasn't been used in the last year or something. 

Those removals should be purges. Purges should remove every instance of settings. I recently had an issue with grub and the resolution wound up being purging grub and reinstalling. Additional issues cropped up because purge did not remove every grub setting. That was finally resolved by cancelling out things installed by boot-repair that in the end were not needed, but should have been removed in a purge.

Oh, I should add that I save a new get-selections every day with a script that also does updating and runs Bleachbit against the settings in Bleachbit. I try to keep my system clean, but when I try to fix something, sometimes I throw the spaghetti against the wall and see what sticks. I am hoping for a way to remove the unused, but also unwanted spaghetti.

---

### Post by roma.parabellum on 2018-10-20
Thanks! I am thinking to search some time, maybe I will be able to fix this problem with x-server start at booting without reinstalling (however it starts wirh Ctrl-Alt-F1). Then I am going to backup my home folder, switch to win10, clean partion with ubuntu and install from scratch using usb. Also I see you are installing nvidia driver 346, yesterday I updated it to 396 - saw at one askubuntu questions this recommendation for similar problem (did not help).
Anyway many thanks for such detailed instructions.

---

### Post by raccoonstrait on 2018-10-20
That is an old sample of the re-install portion, you are correct that a newer version would be appropriate.

Raccoon Strait

---


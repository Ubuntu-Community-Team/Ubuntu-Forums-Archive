---
title: "Skype Problems and Remastersys Advice"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by throese on 2011-03-25
I had recently updated my laptop, but now Skype won't work at all. The Log-In window won't come up anymore no matter how many times I click on the Skype button in my dock OR Internet > Skype. I don't know the name of the update and I've already tried uninstalling and then re-installing at least five times minimum but no luck on it working.

Would someone please be kind enough to help me out and solve this problem?

My last resort is to re-install Ubuntu (my custom iso) that I have that backed up all my programs and settings (I don't back up personal files/documents. I exclude those).

--------------------------------------------------------------------------

For those who use Remastersys:

When backing up the system, back up your personal data on an external drive of some sort, whether it's a hard drive or a flash drive, just back it up onto something external or a server. Then go into the Remastersys program via System > Administration > Remastersys

Then go to Modify and go to Exclude and exclude the following:

/home/USERNAME/
/home/USERNAME/Documents/
/home/USERNAME/Music/
/home/USERNAME/Videos/
/home/USERNAME/Downloads/
/home/USERNAME/Example/
/home/USERNAME/Public/

and anything else within your /home/USERNAME/ directory

Everything within my /home/USERNAME/ directory is a little over 8 gigs, which is why the ISO file was too large. If you do as I advised (back up personal data onto external device or on a server or shared folder) and exclude the above folders, the ISO file will be 1 or 2 GB, depending on how many programs you have on your system at the time of the backup.

My backup is 1 GB exactly, that's just with programs and personal settings for the programs.

---

### Post by gordintoronto on 2011-03-25
You might try opening Accessories/Terminal, and pasting this command:
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

At least, it might show an error message which can help you figure out what is wrong.

---

### Post by throese on 2011-03-25
I did the commands and I got this:

---

### Post by gordintoronto on 2011-03-26
I have no idea what might have caused that, but now you have something you can Google.

---

### Post by throese on 2011-03-27
gordintoronto: So you have never seen this problem before?

---

### Post by mörgæs on 2011-03-27
If you hide the configuration folder ~/.Skype (rename it to  ~/.Skype_old, for example) can you then start Skype?

---

### Post by throese on 2011-03-27
I don't even have the hidden Skype folder. Wonder where it could have gone. Guess I'm gonna have to re-install, or allow someone to Remote Desktop into my system to see if they can fix it.

---

### Post by gordintoronto on 2011-03-27
I have not seen this problem before. Skype has always worked for me, since I discovered the "preload" thing, and got my webcam working in 10.10.

By default, Nautilus (the file manager) does not show hidden folders. There's a setting to change that: Edit/Preferences. But you probably knew that.

You've never mentioned what version of Ubuntu you are using.

The final post in this thread might help you:
[http://forum.skype.com/index.php?showtopic=229201](http://forum.skype.com/index.php?showtopic=229201)

---

### Post by throese on 2011-03-27
I use: Ubuntu 10.04.2 LTS

---

### Post by oODeanOo on 2011-04-18
Same here 10.04 32bit and almost daily Segmentation Fault error with the 2.2 Beta of Skype... Through the somewhat brash developer on the Skype forums I've narrowed it down to the Skype file in \usr\bin getting corrupted as using GTKhash showed that the hash has changed.

Anybody got any ideas why this may happen?  I've remove the helpers for Skype from Kupfer and AWN and it still happens.

Dean

---

### Post by oODeanOo on 2011-04-22
My segmentation fault errors with Skype 2.2.0.25 is caused by Prelink.

The solution is to exclude the Skype binary from Prelink.

To fix you need to do the following

sudo gedit /etc/prelink.conf 

add the following line and save.

-b /usr/bin/skype

Hope this helps 

Dean

---


---
title: "Upgraded and totally scr'wed up"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by markymark64 on 2011-04-29
I know this has to do with my video drivers. When I upgraded to 11.04 I had a few issues and restored my profile from a backup. Unfortunately, I kept getting the same errors I was seeing with the beta version in that it didn't recognized my video drivers. Well, I had a few specific errors initially and restored my backup and rebooted. Well after spending hours downloading all of my apps because they were lost with the upgrade I thought I got everything setup and working perfectly. Ok, so i changed my mouse cursor and something told me to check for new or additional drivers. My video display said it was active but not in use. Now when I boot up to ubuntu I have to wait about 30 seconds while watching a square box travel across my screen telling me that it can't determine the input. If I wait I get a desktop but with no top or bottom menus. In other words I have no way to get to the synaptic package manager or to a terminal window. This is really frustrating because I have spent the last three hours downloading and reinstalling applications. 

Is there any way I can fix this problem and restore my desktop?

---

### Post by markymark64 on 2011-04-29
Too many problems with this release so I have rolled back to Ubuntu 10.10.

---

### Post by Cotopaxi on 2011-04-29
Sorry, how do you roll back to 10.10?

I am totally screwed up and I do not know how to reverse the whole thing!

Thanks!

---

### Post by Cotopaxi on 2011-04-29
I just found the installation CD for the 10.04 version

Can I just put that CD in and make a clean install, preserving only the home partition?

Thanks for your help!

---

### Post by dino99 on 2011-04-29
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by mbott on 2011-04-29
> **Cotopaxi said:**
> Sorry, how do you roll back to 10.10?

I am totally screwed ...

You didn't back up your system before upgrading?  For me, Clonezilla had me restored in 15 minutes.

-- 
Mike

---

### Post by markymark64 on 2011-04-29
Cotopaxi, if you already have 3 partitions please don't reformat them in the install of 10.10. 

You probably have 3 partitions. One is for your swap file, the second is for the root and the third is your home partition for all of your software. 

I'm not sure what your system looks like or how familiar you are with installing Ubuntu. I'm pretty new to this myself but got the hang of it very quickly. Please forgive me if I'm talking down to you.


When you load the live cd for 10 in your pc  and choose the option to select where you want to install it you're eventually shown a screen with all of your partitions. I have my ubuntu installed on a separate partition from windows. If yours is the same here's what I did to reinstall 10. 
When you are going through the process of installing 10 you want to modif modify each of the 3 partitions so that they say ext3 or ext4 but don't format if they contain data! The format option is a checkbox that you see if you choose to modify any of the partitions. You only want to modify the one's that you have set up for ubuntu. So for your swap partition you would simply choose the swap from the drop down and choose the option above it for ext3 or ext4. The root directory would be ext3 or ext4 with no format and you want to choose the / from the dropdown at the bottom. Lastly, your home directory, which is the largest you choose ext3 or ext4 and from the drop down choose /home. Remember don't check the format on any of these or you'll lose data. 

Also, have you backed up your data to a safe location just in case of a problem like this one? 


Does this help you any? If not, please write back or create a new thread. I know there are plenty of people that will chime in to help you out.

---


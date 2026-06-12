---
title: "Installing Xubuntu over Mint in dual boot system"
date: 2019-09-22
forum: Installation &amp; Upgrades
---

### Post by nipplewise on 2019-09-22
This is where I am stuck.
I want to install Xubuntu over Mint and preserve Windows 10.

---

### Post by uRock on 2019-09-22
Select the EXT4 partition and set it to use "/" and it will install Xubuntu in that partition. All data in that partition will be destroyed. Be sure to back up any data and it is always good to back up Windows, as well.

---

### Post by nipplewise on 2019-09-22
How do I set it to use "/"?
I am trying to somewhat replicate this on Virtualbox so I can see the options without making mistakes.
I think I can right click, select **Change...**, but in **Use as:** I have many options. Which one of them do I choose?
And do I have to tick **Format the partition**?

---

### Post by Dennis N on 2019-09-22
use as ext4 journaling file system.
when overwriting a previously used partition, you should check format box.

---

### Post by nipplewise on 2019-09-22
Thanks for the answer.
But it already is ext4.
Does it mean that I only have to check the format box and I can then proceed with the installation?

Edit: Because in the first answer I am told *Select the EXT4 partition and set it to use "/" *but I don't understand the second part of the quote.

---

### Post by uRock on 2019-09-22
You're selecting "/" as the mount point.

---

### Post by nipplewise on 2019-09-22
I do not have such option.

---

### Post by uRock on 2019-09-22
> **nipplewise said:**
> I do not have such option.

You're good to go without it then. I've only once reinstalled over another distro and that distro's installer wasn't as good as Ubuntu's at noticing a single partition install.

---

### Post by nipplewise on 2019-09-22
Oh, I did have that option!
But I had to first pick one from **Use as:** for it to show up.
I successfully installed Xubuntu.
Thank you both for your help.

---

### Post by uRock on 2019-09-23
Rock on! :guitar:

---


---
title: "Ubuntu won't work on Windows 7 laptop"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by Pandanon on 2011-06-16
Hello,

I have this problem everytime I install Ubuntu 11.04,
The problem is that when I restart after installing Ubuntu in Wubi inside Windows 7, it finishes the Ubuntu install and then it goes back to the login screen of Windows 7.

Then when I restart my laptop again and startup Ubuntu I can get to the login screen of Ubuntu but as soon as I login, I only see the background and it stays there..

I have tried re-installing it several times, I have tried it with a CD and Wubi.

I also tried restarting it several times before finishing the Ubuntu install, but nothing seems to work.

I have no clue of whats wrong and I do not know how to fis it, help asap will be appreciated and if you can try and explain it somewhat in a simple tone and understandable steps because I am not so familiar with Ubuntu.

Thank you in advance,
- Roy

---

### Post by Rubi1200 on 2011-06-16
Hi and welcome to the forums :-)

Since you have the CD, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by sanderd17 on 2011-06-16
Maybe something easier first: When you login (at the screen where you have to fill in your password), choose at the bottom of the screen an other environment and see if it works.

---

### Post by Pandanon on 2011-06-16
> **sanderd17 said:**
> Maybe something easier first: When you login (at the screen where you have to fill in your password), choose at the bottom of the screen an other environment and see if it works.

Ooh sorry I forgot to mention that I already did that I tries several ones, the classic one and the one without effects or something but it didn't work..

---

### Post by arpanaut on 2011-06-16
Specs. of laptop?  especially Re: graphics card

---

### Post by Pandanon on 2011-06-16
@ Rubi1200
Thank you :)

I tried running it from the disk in demo mode but looks like it's not working it just stays on the Ubuntu loading screen and stops loading and that's it.. Ooh and my cd-drive started making weird noises so I turned of my laptop.

@ arparant
not sure what my graphics card is..
But here's a screenshot when I view properties of my Computer :
[IMG]http://img14.imageshack.us/img14/549/75684331.png[/IMG]
Hope it helps :)

---

### Post by sanderd17 on 2011-06-16
It's normal that your CD drive makes weird noises. 

And for the specs that are needed. What model is your laptop?

---

### Post by Pandanon on 2011-06-16
> **sanderd17 said:**
> It's normal that your CD drive makes weird noises. 

And for the specs that are needed. What model is your laptop?

It's an eMachines (It's a branch from Acer I think) E625

---

### Post by Rubi1200 on 2011-06-16
Hi,
the screenshot does not contain the information we need. No matter, from your description, this is almost certainly a graphics issue.

Take a look at this link and use the instructions to set boot options on the LiveCD. I recommend you try nomodeset to begin with. If that works, follow the rest of the instructions I posted previously.
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by Pandanon on 2011-06-16
Alright i'll try that :)

---

### Post by Pandanon on 2011-06-16
I tried to do what was in the link but I couldn't find the options..
I did find a menu where I could choose Demo mode, graphics safe mode etc. But that didn't work either.

I will try again tomorrow because I have to go to sleep now I have to get up for work in 6 hours :p

Thank you for all your help so far :)

---


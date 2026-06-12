---
title: "Locahost login after installation"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by yashg98 on 2012-06-22
I recently installed Ubuntu 12.04 on my computer with a USB stick cause I don't have a CD drive. The normal  ISO didn't work, so I used the text installer and completed all the  steps somehow. Eventually it showed "Finishing  Installation" and rebooted and I was met with a prompt saying "Localhost login ttly" or something.

I searched some old forums and tried out the login and password as root,  guest, ubuntu etc but all in vain. I used the rescue mode and tried to install ubuntu desktop with 
sudo apt-get install ubuntu-desktop

it says it is not installed and attempts to install. So I think I found
the problem. The desktop is not istalled. But when I run this command it 
says it wants some disk space. I press enter and then it asks to insert 
the ubuntu CD and press Enter again. But as I told, I don't have a CD drive,
so can anyone help me out?

---

### Post by dino99 on 2012-06-22
check that the bios is set to boot on hdd

open a terminal & run:

gksu gedit /etc/apt/sources.list

select the line talking about cd and comment it out, by adding # in front of this line

then save and exit from gedit. Then run:

sudo apt-get update
sudo apt-get install  --fix-missing
sudo dpkg-reconfigure -phigh -a
(be patient, it can take a while)

---

### Post by yashg98 on 2012-06-22
I can't enter Ubuntu, but can I do what you told in a Rescue mode shell?

---

### Post by sunson565 on 2012-06-24
> **yashg98 said:**
> I can't enter Ubuntu, but can I do what you told in a Rescue mode shell?
I have a very similar problem, please post the solution if you found it out

---

### Post by sunson565 on 2012-06-24
I re created the live usb with a ubuntu 12.04, using usb creator, booted well in the first time, I did some changes (installed video codecs and main menu u torrent) then rebooted, ! it didn't boot ! please see the screen shot 
[IMG]http://i807.photobucket.com/albums/yy358/zaprotta/screenshots/1.jpg[/IMG]

---


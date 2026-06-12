---
title: "Installed Lubuntu 19.04 but the theme looks like ubuntu."
date: 2020-03-07
forum: Installation &amp; Upgrades
---

### Post by damir2020 on 2020-03-07
Hi there!

I'm a total noob to Lubuntu / Ubuntu. I know the name but today I installed the OS for the first time in my live :D Looks good btw! 
Anyways, a friend asked if I could "fix" his 10+ years old PC, I replied "I'll try!", finally got some time so I took a shot today, after googling around I learned that Lubuntu might be the best OS for this system.

So I downloaded Lubuntu 19.04 and installed it on the PC. I was prompted with the question which additional software to install, instead of checking the boxes I pressed enter and accidentally continued installation. 
After the installation, it loaded Lubuntu and asked for login in the terminal instead of a user login screen. So I figured out it needs desktop installed, so I did with these commands:

sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get -y install ubuntu-desktop

After this was done, I indeed get a login screen & desktop, all looks good, but it looks like Ubuntu (see attachment) instead of Lubuntu (see attachment). So my questions are:

- How is this possible / What went wrong or not?
- Is this indeed Lubuntu or Ubuntu?
- Does this "Ubuntu" desktop effect performance? -> Is the Lubuntu dekstop faster?
- How can I fix this?

Looking forward to your replies.

Thanks

---

### Post by coffeecat on 2020-03-07
Welcome to the forum!

> **damir2020 said:**
> So I downloaded Lubuntu 19.04 and installed it on the PC.

Both Lubuntu and Ubuntu 19.04 went end-of-life in January this year. No more updates or security patches. I'm surprised you were able update and install something. The repositories must still be open but, if so, they will close very soon. I suggest you start again with 19.10. Be aware that this is an interim release, only supported until July of this year. 20.04 will be released in April, which is LTS (long-term support) supported for several years. You will be able to upgrade from 19.10 to 20.04 before 19.10 goes eol.

> **damir2020 said:**
> 
sudo apt-get -y install ubuntu-desktop

That explains  why your first screenshot shows the Ubuntu (gnome) desktop. You installed the Ubuntu desktop on top of Lubuntu, and can choose which to use at the login screen.

> **damir2020 said:**
> 
- Does this "Ubuntu" desktop effect performance? -> Is the Lubuntu dekstop faster?


Post details of your hardware and forum members will be able to give their opinions on the pros and cons of the two versions, and whether your hardware adequately supports the more resource-intense Ubuntu.

---

### Post by guiverc on 2020-03-07
My desktop is a 2009 year dell optiplex 960, and my install was originally a Ubuntu system (GNOME), on which I added Xubuntu (XFCE), Lubuntu (LXDE originally, now LXQt) and Ubuntu-MATE (MATE).  I would suggest adding all of them (there are complications as you add more desktops that can take away from benefits), but my point is all run.
I can use GNOME on my system fine, but I prefer the lighter desktops of XFCE (Xubuntu) & LXQt.(Lubuntu). Being lighter they run 'faster' which makes them nice, but personally I just prefer them.

Multiple desktops will mean
[LIST]
[*]upgrades will be larger, as in my case I get updates for all four desktops, on your system you'll get all Lubuntu & Ubuntu desktop upgrades, this means more bandwidth as far as downloads, plus you need more space to install said upgrades (do you have bandwidth quotas? large or small disks etc)
[*]menus are more complex, for editors you'll see Featherpad (Lubuntu) & Gedit (GNOME), for File Manager you'll see Nautilus (Files for GNOME) & Pcmanfm-qt (Lubuntu) etc... On my system I have four alternatives for each
[*]there are costs to stability (esp. as you add more as they can interfere with each or create clashes, you don't notice it with only two, but after 3 issues can occur.. It took me a lot of experimentation to get my '4' just right..
[*]when release-upgrade time comes, you'll need a lot more free disk space
[*]Lubuntu (LXQt) is Qt based; so GNOME (GTK+) apps won't be as efficient memory wise, and vice-versa. If you have lots of RAM/memory this isn't an issue, but on limited RAM sizes this cost will negatively impact performance, esp. with programs that need loads of free RAM.  My system has 8GB so I ignore that, but it matters more if you have 4GB of ram or less (esp. 2gb or less).
[/LIST]

I'll stop there..   

I like multiple desktops, in fact LOVE it.  I decide at login which will suit what I want to use depending on what I want to accomplish, or my mood. Mostly I choose LXQt (Lubuntu) or XFCE (Xubuntu), but for a newbie I'd probably recommend just a single DEsktop to start with, as the complications cost will likely outweigh the benefits.   My 2c


I'd also start again & re-install.   A `do-release-upgrade` required to move your 19.04 system to become a 19.10 system will take far longer, so save yourself the time and just start again...  Installs are relatively fast so I'd have a play and work out which DEsktop both performs well on your hardware, and which just *feels* right for you. Every desktop has it's positives and negatives, but it's mostly like choosing chocolate, vanilla, strawberry or any flavored ice-cream; it's what flavor just* tastes* best to you; your choice.

---


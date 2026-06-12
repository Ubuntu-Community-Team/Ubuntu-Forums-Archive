---
title: "Everytime I run a software update,my system fails on rebot"
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by breezypt on 2013-04-21
I was back to 12.10 from 12.04 after a failed 12.04 update last week. A Few days ago 12.10 came out with an update. I ran the update, rebooted into an endless loop of errors AGAIN!. Every single time I run an update my OS is unbootable and I have to reformat and reinstall, start all over again. I have 7 email accounts I have to register into again, I have my bookmarks luckily backed up on my phone so I sync them back I have 5 USB sticks I put important documents on in case of an update release, I have graphics saved on old disks that lucklily I got back. But I am sick of going through the motions of reformatting

What in the world is the reason why I have to reformat every single time. This is about the 10th time I have installed ubuntu. I like the OS I was really liking 12.10 extra features before you broke it again. I don't know where  to turn here. It is not once or twice or even three times. This is EVERY update, you break a perfectly working system.

Here are my specs, since they dont allow or feel the need to have it in the signature I'll post it here for you, if you see a piece of hardware that is incompatible tell me and I won't bother any one anymore. I am a self reliant person, I don't like yelling boohoo to message boards every time something goes wrong I usually fix it myself. This build is my own and has been running without problems for 2 years now. I just got done runninig memory tests and the memory is fine forget memory. I ran the CD on it all night long! ZERO errors!

Power supply: Corsair 400 Watts
CPU: Intel Core2Quad Q8400 2.66 GHz
Motherboard: Gigabyte GA-EP45-UD3P Rev. 1.6 FE BIos F12
GPU: NVidia GTX 650
2 Westrern digital 500 GiB hard drives
Memory: G Skill DDR2 4 GiB

I am using the 310 driver form NVidia because the one provided with Ubuntu deos NOT provide hardware acceleration. Everything else is what you provided in your updates.

I don't want to leave Ubuntu but I am running out of hair strands.

---

### Post by ajgreeny on 2013-04-21
What does "my OS is unbootable" mean; does it boot but leave you with a black screen instead of the GUI, or does it not even get to the booting stage?

---

### Post by breezypt on 2013-04-21
It goes into the boot up process, for a few lines of OK, then just stalls. After several reboots, it would boot me back into the log in  screen, then I would sign in and it would do the same thing again run a few lines of code them bring me back to the login screen after it looked like it was going to load the OS.

I apologize to the forum if my anger sounded like it was aimed at them , it wasn't but I managed to run Mac OSX on homebuilt computers for over 4 years and had to reformat once, which I can't complain about. Yes I paid for the software but it explicitly said in the eula to run it only on Mac Hardware. But this is not the case here, especially in the case of LTS versions. If this is exprerimental software and I am here to find bugs then let me know so I at least I am not expecting a somewhat reliable system. I have not ran an update since I started using Ubuntu including  Mint versions (which are bases on the same OS) where I didn't have to reformat aftwerwards. So you can snese my frustrations. When an update pops up I'm afraid to let a security update run!

---

### Post by matt_symes on 2013-04-21
Hi

It sounds like you have more than one issue here.

> 
It goes into the boot up process, for a few lines of OK, then just  stalls. 

What text is displayed on the screen when it stalls ?

> After several reboots, it would boot me back into the log in   screen, then I would sign in and it would do the same thing again run a  few lines of code them bring me back to the login screen after it looked  like it was going to load the OS.

This sounds like X is crashing and taking you back to the login screen.

You say you are using the nVidia drivers. 

Where are you getting them from ? How are you installing them ?

Are you using any PPAs ?

Can you boot into an older kernel ? If so, do you have the same issue ?

Really we need to see you log files to see exactly what is happening on your machine and to see why you are getting the errors you are getting.

Can you boot into a liveCD/USB, mount your root directory on your hard drive and connect to the internet from a LiveCD/USB.

If so then open a terminal and type

```
sudo apt-get install pastebinit
```

then type

```
pastebinit -b http://sprunge.us <mount_point_of_root_directory>/var/log/syslog
```

Check the url returned has something in it and if it does then post back the URL here.

We will also need another log file at some point but let's check that one first.

Kind regards

---

### Post by breezypt on 2013-04-21
Matt_ Thank You for your response for help, I'm going to copy and paste your code then print them out for the next time it happens.

what was happening in 12.04 was like I said as the X system was loading it would stall on errors....after the updates. I put in secure 12.10 with bootrepair, it repaired  grub, then I booted into 12.10, I could not get into 12.04 any more so I said heck with it and installed 12.10.
I set everything up in 12.10, all my music files, graphic, bookmarks, etc you know the deal...along comes another update, so I let it installl the update...it does the same thing again. so I rebooted a few times after waiting for like 30 minutes for the error to hopefully clear. The reason for that is that after every reboot, I was getting a stall out in a differrent error on the screen. I'm sorry I didn't write them down I was past frustration.

Anyway I did another hard drive reformat and am now back in 12.04 with everything working...if upon the next recomended update I will do your steps exactly as you recommended. I'm always more than willing to learn, thats why I don't want to just leave Ubuntu I have a lot of time involved learning the system, and I do contribute with some solutions that do help other people in some threads.

As for you question of drivers.I down loaded the 310 driver from the NVidia website , marked the file as executable, went into tty1 and stopped lightdm, then ran the installer of the nvidia driver. There is a major difference in speed between the nvidia driver and the one supplied by Ubuntu there just is, I have no idea why.

Repositories, I just added one just now launchpad for Cairo, and it is running fine. This is the point where I had my OS after the last 12.04 update screwed me. I definately remember why on that one it had an update to the nouvoue driver I should never have let the OS take, I learned my lesson the hard way on that one. But this last update for 12.10 had nothing but a few security updates, and nothing about nouvoue or the video drivers. Which perplexed me slighly I thought I was safe.

I feel like Dustin Hoffman in the Marthon Man movie in that chair with that evil sob torturing him saying..is it safe, is it safe?? I'm afraid to take a security update.

But like I said I'm sticking to this see it through, and will follow your recs.I will send it to the the forum to show you what went down? If or when it does...:)

---


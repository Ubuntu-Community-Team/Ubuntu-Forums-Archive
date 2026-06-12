---
title: "Installation problems/questions"
date: 2017-02-28
forum: Installation &amp; Upgrades
---

### Post by lawrence-joy on 2017-02-28
I had Ubuntu 16.04.1 LTS loaded and I had been using it. The software updater indicated 16.10 was available and so I answered in the affirmative to install it. Then I saw that 16.10 seems to be an intermediate version because April 2017 is an ending date for it. So I downloaded 16.04.2 LTS, or thought I did, as at the end there was a screen with a button that said "extract...", which I clicked on and that opened another screen that had another button that said "extract...", which I clicked on. That seemed to finish the job as there was a message that said thanks for downloading... When I checked with the terminal command "lsb_release -a" it says it's version 16.10. I am confused. How come 16.04.02 LTS didn't overwrite 16.10? Should I stick with 16.10? What would happen come April this year? Is 16.04.02 LTS on my computer? If so, how do I make it the operating system?

---

### Post by Autodave on 2017-02-28
Simply downloading 16.04 will not install it. I do not believe that you can roll back to 16.04: you would have to do a new install.  BACK UP FIRST!!!  You could just continue using the 16.10 if it is working OK for you. Every 6 months you would then update to the next version (17.04, 17.10, 18.04). 18.04 will be a lo9ng term release, so if you can keep updating to that, you can stop there for a few years. :-)

If you are going the route to keep updating until 18.04 is on the machine, stay current with the updates!  You cannot ship one!

---

### Post by howefield on 2017-02-28
> **lawrence-joy said:**
> Then I saw that 16.10 seems to be an intermediate version because April 2017 is an ending date for it.

Actually, 16.10 is supported till July this year, not April.

> So I downloaded 16.04.2 LTS, or thought I did, as at the end there was a screen with a button that said "extract...", which I clicked on and that opened another screen that had another button that said "extract...", which I clicked on.

Sounds like instead of saving the downloaded iso image you have opted to open or run it after downloading hence the offer to extract, this would not have any bearing or impact on your installed OS.

> Should I stick with 16.10?

You've got till July to decide ;) 

> What would happen come April this year?

You'll be offered 17.04.

> Is 16.04.02 LTS on my computer? If so, how do I make it the operating system?

Sounds not, the terminal command should confirm what uname has already said.

```
cat /etc/*-release
```

The only realistic way of getting back to 16.04.2 would be a clean install, although you can install directly into the existing partitions and not marking for formatting will leave your /home folder intact. It goes without saying that important data should be backed up first.

---

### Post by lawrence-joy on 2017-03-01
I just had a whole message disappear because I had it typed out and then clicked on "Reply to Thread". I guess I should have clicked on "Post Quick Reply". I will type it again, but it won't be the same as the original.

Okay, my choice as to whether to stay with Ubuntu 16.10 and upgrade when necessary or try to download a clean 16.04.2 LTS installation. Is there a command to save "important data" to a USB memory stick? When I downloaded 16.04.2 LTS there were two choices, "Install" or "Save" without any further explanation. I guess "Install" means to install temporarily and "Save" means to install to the drive. Thanks for the command "cat /etc*-release". I didn't know this previously.

I have two other problems. When I go to the fat up and down arrows icon in the upper right corner of my screen, I click on Ethernet1 and get a "Connection established" flashed that immediately turns to "Disconnected". I can not get to any websites with the message that appears "Firefox can not get to the server at..." What is going on? I have two solid state drives on my desk top PC, one has Windows 10 OS on it and the other has Ubuntu OS. I can get to the Internet with Google Chrome on my Windwos 10 OS, so I know that I have connection to the Internet.

The 2nd problem is when I click on the "Shut down" icon and either click on "Restart" or "Shut down" nothing happens. I click on the Shut down icon again and get "Error. Received error while trying to log out". I then have to push and hold the on/off switch on my PC until it shuts down. What is going on in this situation?--Tnx.

---


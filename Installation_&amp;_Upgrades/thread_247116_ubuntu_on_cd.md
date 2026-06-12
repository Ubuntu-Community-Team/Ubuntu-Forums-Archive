---
title: "ubuntu on cd"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by Kanga on 2006-08-30
Hello I'm a newbie,
Thought I'd try Ubuntu,I've successfully downloaded it onto cd. Changed the computer's bios to boot from cd, and it tries to read from A drive only, which is the floppy disk. I'm stuck! The a drive was not an option in the bios, only hdd and cd.
Could anyone please help to get ubuntu to run off the cd ?
Thanks.

---

### Post by taurus on 2006-08-30
Exactly how did you burn the iso image to a CD?  I assume you know you need to burn it as a image, NOT data.  In other words, you are not supposed to just copy the whole iso to a CD or unpack it first and then burn the content to a CD...  Maybe that's why your system won't boot from the CD!

---

### Post by Kanga on 2006-08-30
Its been burnt by cd burner xp pro 3, downloaded the md5summer, and the md5sum for Ubuntu, as per the instructions. The dvd/cd drives work, and I can see the Ubuntu background with the Firefox and Thunderbird included with it, when in Windows xp.
I think its just that the computer boots from the floppy disc (A)and not the cd, even though its been chosen in the bios.

---

### Post by Kanga on 2006-08-30
Ahhh!
Just worked it out, duh!
The instructions I was following said to leave the disc in the drive after burning it, change the bios and reboot.
Now the disc was in the cd/dvd re-writer drive and not the dvd rom drive. Guess which one was the bootable drive ?
So now I can access the "live" cd.
What I cant do now is access the internet with Firefox.
I use Firefox on Windows xp, no problem.
So, please, What do I need To do now?

---

### Post by randell6564 on 2006-08-30
> **Kanga said:**
> Ahhh!
Just worked it out, duh!
The instructions I was following said to leave the disc in the drive after burning it, change the bios and reboot.
Now the disc was in the cd/dvd re-writer drive and not the dvd rom drive. Guess which one was the bootable drive ?
So now I can access the "live" cd.
What I cant do now is access the internet with Firefox.
I use Firefox on Windows xp, no problem.
So, please, What do I need To do now?

Glad ya got it going!  But how are you setup for internet connection?  Are you hardwired directly to a modem/router.  Are you wireles, Ethernet, DSL,Dial-up, what?

---

### Post by DLWood on 2006-08-31
I've got exactly the same issue.  I have no problems accessing the internet via Windows XP.

I have a "direct connection" when looking at my Firefox preferences under Windows.  I had the same thing checked under Ubuntu & Firefox, but it doesn't access the internet when using the Live CD.

I have DSL with an Actiontec DSL Gateway.

What now?

---

### Post by randell6564 on 2006-08-31
> **DLWood said:**
> I've got exactly the same issue.  I have no problems accessing the internet via Windows XP.

I have a "direct connection" when looking at my Firefox preferences under Windows.  I had the same thing checked under Ubuntu & Firefox, but it doesn't access the internet when using the Live CD.

I have DSL with an Actiontec DSL Gateway.

What now?

I'm going to assume that you are not using a router since you did not mention it.

Boot into Ubuntu.  when you get to the Desktop, go to System>Administration>Networking.

A window will pop up and you should see 'Ethernet Connection', or 'Modem connection', or both.  click on the one that you want and Enable it.  Setup the network stuff if you need to then click ok.  A bar should pop up that is your indication that it is sarching for a connection.

That should do it.  If you have any problems with connecting then I probably can't offer anything more.  I am running Wireless with a broadband connection, so I'm not real familiar with DSL.

Good Luck!

---

### Post by DLWood on 2006-09-01
I think the Actiontec DSL Gateway is a router, but I don't know what to do differently because of that.  I only have one computer and it's hooked up to the Actiontec via an ethernet cord.

Anyway, I did enable the Ethernet connection.  I wasn't sure what to put in the "domain" field.  My provider is "tds.net" and I tried to put that in, but I could tell no difference.

I was able to navigate around the Ubuntu site pretty well.  I'm not sure if that's because many pages were already loaded on the CD or if I was actually connected with the internet.  I was also able to access many Mozilla pages by clicking on the "get started" button on the Firefox bookmarks toolbar. 

It wouldn't let me go very far though.  If I tried to go to the Ubuntu forums, it would just sit and spin.  Same thing happened if I tried to go to any other address (e.g., Yahoo.com)

I tried setting the Ethernet settings manually by taking similar info from my Windows connection screen.  I could match up some stuff there, but not all.

So, I'm still unable to connect with the internet.  Anyone have any words of wisdom to help me configure Ubuntu from the Live CD?

Another clue....I have an Ekiga user name and went through the setup and it seemed fine and even registered my Ekiga account.  I figure something has to be communicating over the internet for that to happen.  But it wouldn't let me place a call to another SIP number.

Thanks for any help.

---


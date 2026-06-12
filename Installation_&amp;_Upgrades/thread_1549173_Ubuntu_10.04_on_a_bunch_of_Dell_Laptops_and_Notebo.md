---
title: "Ubuntu 10.04 on a bunch of Dell Laptops and Notebooks"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by CPL2010 on 2010-08-09
Worked like a charm.  No more XP in the house for any of the kids.:popcorn:

WiFi issues are no longer a problem like in 9.x.  Applying the usual stuff like Firefox:about configuration (ipv6, http,pipeline,etc) and Adblocker Plus make the browser speeds lighting fast.

Three days in and no complaints.  All the system specs as follow.

   [FONT=Arial][SIZE=2]J’s desktop[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]21” DEC CRT monitor [/SIZE][/FONT]
  [FONT=Arial][SIZE=2]1 gig of RAM[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Couple of Seagate hard-drives (100 gig and 40 gig)[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]2.4 Ghz P4[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]WiFi[/SIZE][/FONT]
[SIZE=2]DVD/RW
[/SIZE]
  [FONT=Arial][SIZE=2]128 meg ATI 6800 video card.[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]H’s desktop[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]17 inch monitor[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]512 of Ram[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]20 gig drive[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]1.0 Ghz P3[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Ancient S3 video card, I think it’s got 4-8 megs on it.  Lol[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]DVD/RW drive[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
    [FONT=Arial][SIZE=2]T’s laptop[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Dell Latitude D610[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]1.5 gig of Ram[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]100 gig drive[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Wifi/LAN/Modem[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Crummy intel 915 GM video on board (yuck)[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Battery still has life in it.[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]Wife’s lappy[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Pink Dell 1525 Inspiron[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]2 gigs of ram[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]240 gig HD[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]WiFi/LAN/Modem[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]X1300 ATI[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Battery still has life in it.[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]M’s Laptop[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Pink Dell mini 10[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]2 gigs of ram[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]120 gig HD[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Wifi/lan[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]I think it’s a crummy intel 915[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Battery runs forever.[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]My Laptop[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]Dell Inspiron 9400[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]2 gigs of ram[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]120 HD[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]WiFi/Lan/Modem[/SIZE][/FONT]
  [SIZE=2][FONT=Arial]X1300 video with 256 megs on board[/FONT][/SIZE]
  [SIZE=2]
[/SIZE]
  [SIZE=2]Now to figure out how make a media server, instead of using Windows 2003 acting as a DC and media/patch server.  Anyone have a couple of how to?  I want to give it a try this weekend.

Mostly I'm trying to figure out how to centralize the patch management for Ubuntu.  I want the updates to reside on the patch server in the house and pull patches from there instead of updating from the site on a per desktop basis.  Kind of like how Microsoft has WSUS acting as a central repository.
[/SIZE]

---

### Post by chiafunkito on 2010-08-09
having just upgraded to Ubuntu 10.4 I cannot get any sound or video despite having the hardware attached-any suggestions?

---

### Post by CPL2010 on 2010-08-09
You upgraded?  Or you wiped the disk and reinstalled from scratch after backing up your stuff?

If you havent' got video or audio, my experience so far with Ubuntu is to wipe the drive and start over.  15 minutes to reinstall or 4 hours poking at ALSA and video drivers.

---

### Post by chiafunkito on 2010-08-09
Wiped disc and installed 8.10 then upgraded to 9.04, 9.1 then 10.04

---

### Post by mörgæs on 2010-08-10
> **CPL2010 said:**
> Now to figure out how make a media server, instead of using Windows 2003 acting as a DC and media/patch server.  Anyone have a couple of how to?  I want to give it a try this weekend.


Maybe Mythbuntu is what you want. I have not tried it myself, though.

> **CPL2010 said:**
> 
Mostly I'm trying to figure out how to centralize the patch management for Ubuntu.  I want the updates to reside on the patch server in the house and pull patches from there instead of updating from the site on a per desktop basis.  Kind of like how Microsoft has WSUS acting as a central repository.


Will a proxy server do?


And by the way: Congratulations with you Windows-free /home.

---


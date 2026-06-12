---
title: "mobile ubuntu"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by rockfloyd on 2006-07-17
hi, i've had a successful install of ubuntu for some time now on my internal hdd, but after the drive crashed and i took it in to best buy, the computer guy warned me that my whole box will die sometime soon because of motherboard problems or something. i don't want to risk anything killing my ubuntu partition, so does anyone think it's possible to install ubuntu and grub onto an external hdd so that it can boot from any computer? the reason i'm asking is because i'm not sure if grub installs onto a specific hdd or somewhere else on the computer.

---

### Post by scxtt on 2006-07-17
grub installs in the master boot record of either 1) the 1st disk on IDE or SATA or 2) the master boot record of the drive to which you install ubuntu ... i'm honestly not sure which, and i don't feel like unplugging a disk to find out :p ... as for "boot from any computer" - that's not really realistic unless these other computers have the same hardware ... you probably could get away w/ it, but you'll just start confusing the hell out of your install if the hardware keeps changing, even worse if you switch graphics card vendors (i.e. ATI in one box, Nvidia in the other - that'd be a headache) ...

---

### Post by rockfloyd on 2006-07-17
oh yeah, i understand. thanks for the reply and i guess i'll just have to deal with it if i have to reinstall ubuntu on a new computer (if i end up having to replace my current one)

---

### Post by scxtt on 2006-07-17
please tell me the b.b. 'computer guy' got more specific about your motherboard 'dying' ... seems fishy to me, more like "oh you better get a new computer from best buy" ... and is the HDD that 'crashed' still usable, or is it toast?

---

### Post by rockfloyd on 2006-07-17
hell, for all i know that's might be what he's doing. i didn't check his little name tag to see what position he held, so for all i know he could be making consignment on all the computers he sells. my other reason for wanting to put ubuntu on an external is pure laziness.. i have 3 desktops and one laptop and i think it would be really easy if i could just take the external from computer to computer whenever i want to use ubuntu.

---

### Post by rockfloyd on 2006-07-17
oh i forgot to answer about the hdd.. yeah it still works, but he said that both it and the motherboard were going to fail soon or something. i already know that there are problems with the motherboard because i had to change the location of my dvd burner from drive slot 1 to 2 because of a bad motherboard connection. i just hope that guy was trying to get me to buy another computer and not telling the truth, because i really don't want to go through that hassle...

---

### Post by scxtt on 2006-07-17
if they're networked (or if they all have internet access, i.e. when you're not @ a computer in your network) you can just VNC/XDMCP into your ubuntu box and use it as if you were sitting in front of it ... basically use it as a host and the other boxes as clients ... that's the great thing about linux, is the ability to 'share' the computer so easily ...

---

### Post by rockfloyd on 2006-07-17
that sounds great, but i've never set up a network before and i don't expect you to walk me through it. that's too much to ask of you. do you know where i could find a guide to set up something like that?

---

### Post by scxtt on 2006-07-17
i'm not much of a guide person, i don't keep links to any - so i'm no good for pointing people in the direction of one ... and i don't mind walking you through it - as long as you have the base hardware, it's not hard to get working ... so do you have a router (or at least a hub)?

---

### Post by rockfloyd on 2006-07-17
yeah i have a router.

---

### Post by scxtt on 2006-07-17
are all your boxes plugged into it?  and if so, do you use static routing for IPs or DCHP?  once you've got IPs for them (what OSes are they running?) you can start connecting to them ...

---

### Post by rockfloyd on 2006-07-17
not all of the boxes are plugged into it. i hope that's not a problem. i use dchp for the two boxes that use the router. one is wireless and one is directly plugged in. this box (wireless) dual boots winxp and ubuntu. the other box just has winxp, but i'm going to install ubuntu.

---

### Post by scxtt on 2006-07-17
any box not connected to your router (either wired or wireless) isn't going to be able to connect to any others [which i'm sure you know ;)] ... so it looks like your 1st plan of attack should be assigning static IPs to each box on your network so there's no guessing on IPs after reboots ... it's a cinch to do in ubuntu and XP ... there might be some fiddling w/ your router, but that'd just be basic stuff {probably just port forwarding if necessary} ...

i think you should pick 2 boxes and we'll get them communicating and setup for a graphical login, then you can choose how to use the rest of them ...

---

### Post by rockfloyd on 2006-07-17
yeah i can assign static IPs, i learned how to do that tinkering around with azureus trying to get good speeds. i did a little googling about VNC and i came up with their website. is the free version good enough? it says it doesn't have file transfer. does that mean i can't modify anything on the computer i'm connected to or that i can't take anything from that computer to the one i'm using?

---

### Post by rockfloyd on 2006-07-17
i think i've got VNC figured out, i used Preferences -> Remote Desktop to set it up for VNC. i'm pretty sure it'll work. thanks for your help!

---

### Post by scxtt on 2006-07-17
vnc allows you to view the desktop of a remote computer - so you have the exact same access you would if you were sitting in front of the box ... it doesn't xfer files as ssh/sftp would, it's more like looking through a window (w/ a remote control robot :p) than being inside the house ...

if you're talking about windows, i use(d) RealVNC (as a server and a client) - worked great ...

the "Remote Desktop" is Vino, it's ok, but i much prefer vncserver or x11vnc ...

---

### Post by rockfloyd on 2006-07-17
how's the performance? like will it run painfully slow when i'm using the remote desktop?

---

### Post by scxtt on 2006-07-17
nope, it'll run great over your network ... doing it from the outside will be slower - but it's totally usable ... i use it daily when i'm at work and want to VNC to my computer - of course both connections are fast ...

---

### Post by rockfloyd on 2006-07-17
that's very cool. i look forward to setting it up. oh one more thing, i run mandriva LE2005 on another computer outside the network. will that be able to connect?

---

### Post by scxtt on 2006-07-17
sure will - anything w/ ssh or putty (windows) [to start the server] and vncviewer will be able to make use of it ...

---

### Post by rockfloyd on 2006-07-17
and to start viewing it i just run vncviewer -fullscreen 192.168.0.1:0 through terminal right?

---

### Post by scxtt on 2006-07-17
looks good to me :)

---

### Post by rockfloyd on 2006-07-17
alright, thank you so much for your help. it's because of ubuntu's community that it's so successful. it's so great just being able to make a post and feel sure that you'll be helped. especially if you don't act like an ***.

---

### Post by rockfloyd on 2006-07-17
oops i got censored.

a$$

---


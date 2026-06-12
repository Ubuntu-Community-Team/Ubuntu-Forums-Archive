---
title: "Ubuntu Raid5 or Raidz Nas and Plex media server"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by Ammar577 on 2013-02-17
Dear All,
im a big fan or plex and have been using it since 2009,
at the begging i invested in a 4 bay drobo and filled it with 2TB HDD and it fulfilled my needs for the past few years and its connect via Firewire to my MacMini as an HTPC, i also used the Drobo as my main backup for all my devices (3 Macbook Pros, 2 Macbook Airs, Macmini) and stored all my family photos in it. and it has served me well.

over the past few years i have managed to completely fill my Drobo and now im looking for a solution that will last me for the next 5 years at least.

i have decided to invest in a Home built Nas project since its the best option for my needs and budget.

Now, im looking to build a Nas and add at least 8 3TB drives with raid 5 for raid z, im currently looking to have the following setup:

1) Run Plex Media Server on it and Stream/ transecode to at least 4 clients at 1080i
2) Be a Network Storage (Nas) with excellent speed (which is why im looking at the Raid Option and for protection of my Data im thinking of Raid 5)
3) Be able to back up as time Machine for all my Apple computers
4) have it stored in a save place for connected to Power and My Gigabit Switch for internet and local Network
5) the Ability to stay ON 24/7 with out any issues

i have done some research and currently in the process of purchasing the following Components for my Build:

1) MotherBoard: Supermicro MBD-X9SCM-F-O
2) CPU: Intel Xeon Quad-Core E3-1230V2
3) Ram: 16GB's of ECC RAM
4) Hard Disk: 8 SATA Seagate Barracuda 7200.14 Hard Drive 3TB - 64Mb
5) Case: Fractal Design Define R3
6) SSD: 64 GB SSD for the OS if needed

Can you be kind to advise me on the best OS and way to build my Server?
i have looked at ubuntu server but im not familiar with Linux commands, its it possible to install ubuntu desktop instead and run it as a headless Nas Media server ?

do i need a raid card ? or a sata port multiplier ?

if yes ? which on?

i really need and will highly value your recommendation and advice

Regards,

Ammar

---

### Post by darkod on 2013-02-17
For the raid card vs port multiplier, a popular solution seems to be IBM M1015 HBA card flashed to IT mode. In that mode it only passes the disks so that the OS can control and use them. For raidz this would be the way to go.

If you decide to go with raid5, you can use the raid on the card itself. Note that this solution is rarely useful for raidz or SW raid since you want the disks to be passed through and most raid cards don't do that by default. On the other hand raidz or SW raid seem much better and much more flexible.

If you are not sure about using the ubuntu server version you could use the desktop version, but I don't see that helping much. It depends on the software you want to run and whether it's GUI dependent. For example, if the SW doesn't have GUI even on the desktop version you will have to use terminal, which comes to the same as using the server OS.

raidz on ubuntu (and linux in general) is quite new, you might want to consider something like FreeNAS but it will also depend on any software you want to run on the machine, because FreeNAS might be limited to run it.

With 8 disks I would seriously consider raid6 or raidz2, which means two parity disks and can handle two failures, not one. But that means you lose one more disk as useful space.

---

### Post by Ammar577 on 2013-02-17
darkod,

Thank you for your quick and accurate response, actually im more leaning to the Raid 5 at the moment, as as for the software i plan to run its only Plex Media Server which has  GUI so im not worried about that. and you are spot on i noticed the  IBM M1015 Card is ver popular, so do i need it for raid 5 ? 

and will ubuntu desktop be able to run as a nas in raid 5 and my  software 24/7 ?

im sorry but im honestly completely new to this so please bare with me

---

### Post by darkod on 2013-02-17
Well, you have the option to go with HW or SW raid. For HW raid you will need a card, so it might as well be the M1015. You don't need to flash it if you want to use it for raid.

For SW raid you will again need the M1015 unless the board supports 8 sata ports to connect all disks.

If you configure HW raid with a card, the array is done by the card and its bios, so the OS sees one single device (like installing on a single disk).

If you configure SW raid with mdadm, I'm not sure root can be on raid5, so you might need to configure a small raid1 device for root, and the big raid5 for data.

Note that the advantage of mdadm SW raid is that you can even move the disks on another machine (if your servers breaks down for example), and it will work as long as the actual disks are fine. With HW raid, or fakeraid bios raid, you will have to connect them to identical raid card if the card dies, and I'm not 100% if it will read the existing array even on identical card. That is the problem with HW raid or fakeraid as opposed to mdadm where the array data is part of the OS and is on the actual disks, not in the raid card or the motherboard.

---


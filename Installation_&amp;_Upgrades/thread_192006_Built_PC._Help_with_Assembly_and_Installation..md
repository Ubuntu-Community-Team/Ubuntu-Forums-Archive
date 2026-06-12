---
title: "Built PC. Help with Assembly and Installation."
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by pkunal on 2006-06-08
I built a PC for the first time in my life. (I had experience upgrading).

However, I have an Intel D945GTPLR Motherboard with Pentium D processor.

Question:

There are 2 IDE connectors on board. FDD & Primary IDE. I do not have FDD and will not use that connector. I have configured such that HDD will be the Master Drive and CD/DVD RW will be the Slave on the same ribbon and connected to the Primary IDE. I have read about doing this and am sure atleast it is the right thing to do. Also the BIOS does support such configuration, allowing to BOOT from the Slave device (I READ BUT WILL RE-READ ON THE SAME).

WILL UBUNTU SUPPORT IT? HOW WILL THINGS LOOK ON UBUNTU? ANY IDEAS? Will both drives be detected automatically or will I have to mount the drives myself?

I sill have to start the system but need to do the final checks and pray before I do so.

Please let me know.

---

### Post by soze on 2006-06-08
[QUOTE=pkunal]I built a PC for the first time in my life. (I had experience upgrading).

However, I have an Intel D945GTPLR Motherboard with Pentium D processor.

Question:

There are 2 IDE connectors on board. FDD & Primary IDE. I do not have FDD and will not use that connector. I have configured such that HDD will be the Master Drive and CD/DVD RW will be the Slave on the same ribbon and connected to the Primary IDE. I have read about doing this and am sure atleast it is the right thing to do. Also the BIOS does support such configuration, allowing to BOOT from the Slave device (I READ BUT WILL RE-READ ON THE SAME).

WILL UBUNTU SUPPORT IT? HOW WILL THINGS LOOK ON UBUNTU? ANY IDEAS? Will both drives be detected automatically or will I have to mount the drives myself?

I sill have to start the system but need to do the final checks and pray before I do so.

Please let me know.[/QUOTE]

This should be fine.
I would recommend that you set the jumpers on both drives to "cable select" mode, this will keep your future aggravation levels to a minimum (if the drives are new, it's mostly likely the default anyway).

Just make sure your bios has the CD as the first boot device and the HD as the second and you should be good to go.

(Just make sure you remove the live cd after the install (-:)

---

### Post by wpshooter on 2006-06-08
Pkunal:

IMO, you should install your hard drive on the primary motherboard controller connector and set it as master and then install your CD-RW drive on the secondary motherboard controller connector (on a separate ribbon cable, of course) and also set it as master.

I believe that will work better for you than the way you described.

All things being equal, if you have a good download and burn of the RELEASE version of Dapper Drake Ubuntu it SHOULD detect and automatically mount your drives.  You will, of course, have to partition your hard drive once you start the Ubuntu installation from the install icon on the Ubuntu desktop.

Post again if you need any further help.

Hope you have a great time with Ubuntu.

---

### Post by pkunal on 2006-06-08
wpshooter, you did not understand my query.

I DO NOT HAVE A SECONDARY IDE CONNECTOR ON BOARD. That is the reason why I have to do Master/Slave Configuration.

Strangely the board does not even have a connector for the AUDIO CABLE from DVD/CD Drive. I read up on Intel's website and they mention that is not needed anymore as all audio is Digitized. 

Am just worried about UBUNTU detecting everything and still have to confirm on the BIOS, If it boots from the Slave Device..I assume it should cause there are not many options.

If anyone has D945GTP boards please confirm this.

---

### Post by wpshooter on 2006-06-08
[QUOTE=pkunal]wpshooter, you did not understand my query.

I DO NOT HAVE A SECONDARY IDE CONNECTOR ON BOARD. That is the reason why I have to do Master/Slave Configuration.

Strangely the board does not even have a connector for the AUDIO CABLE from DVD/CD Drive. I read up on Intel's website and they mention that is not needed anymore as all audio is Digitized. 

Am just worried about UBUNTU detecting everything and still have to confirm on the BIOS, If it boots from the Slave Device..I assume it should cause there are not many options.

If anyone has D945GTP boards please confirm this.[/QUOTE]

Sorry.  What vintage is this board ?  I assume it is ide and not SATA ?  Are you positive that it does not have a secondary IDE controller ?  But in any case if you have only one controller, make hard drive master and CD slave.  Personally, I would not use cable select.  The only real test is to give Ubuntu a test install.  I have found that the new RELEASED version of Dapper Drake installed from the DESKTOP CD download goes very quick when compared to the install time of the previous versions of Ubuntu.

Good luck.

---

### Post by pkunal on 2006-06-08
wpshooter, Intel D945GTPLR does support SATA discs. Infact 4 of them and can configure them in RAID.

Anyways I wanted this computer to be my Entertainment PC in my Living room, with UBUNTU (FREE) instead of Windows XP ($200).

I want to keep it simple and bought an OEM Seagate 160GB HD (Barracuda 7200.9) which does not have a SATA interface???? Does mention it supports SATA...I did not get involved into any further technical details. Frankly I got it for cheap ($30) and a decent speed & size for my recreational/entertainment use. I dont think I should complain unless it is borken cause there are No Return on this item.

Anyways it will be relieving to know the Booter supports booting from the SLAVE DEVICE. AND I AM NOT SELECTING JUMPERS FOR CABLE SELECT ON HD & DVD drives. AS PER SUGGESTIONS ABOVE, I WILL KEEP THEM IN MASTER SLAVE CONFIGURATION.

---


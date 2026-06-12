---
title: "Switch from SuSE 9.2 to Ubuntu 7.10 Gutsy"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by kjmorris on 2007-12-02
My SuSE Pro 9.2 installation was "long in the tooth" a year ago and now is positively ancient and I need to upgrade. SUSE has worked dependably but not perfectly for me but is past its useful life. It has become very sluggish and I'm plagued with lag time on just about everything that I do. I have a CD of Ubuntu 7.10 Gutsy that I want to install. I have a P4 2.8 gHz system with 1 GB of  RAM and two 80 GB HDDs - one with Windoze XP that I rarely use and the other with SuSE Linux 9.2. I can't afford any hardware upgrades at this time, except that I may inherit some additional RAM.

I would greatly appreciate any guidance about moving from SuSE to Ubuntu. In the past, I have simply backed up my data and gone into Windoze and deleted my Linux installation using Partition Magic. Then, I popped the CD or DVD into the drive and did a fresh installation. I would like to make the maximum amount of correct choices during installation so that I don't have to fiddle too much later -- I'm waaaayyy behind on some projects and need to get productive very quickly.

Here are some of my considerations:
1) I am a writer and consultant. I work daily with Evolution, oOo, Firefox, and gEdit. 
2) I frequently use Acrobat Reader, k3b, GIMP, gFTP, and XMMS, although I don't do anything fancy with any of these.
3) I have an Iomega Zip 250 drive (I have loads of old data on Zip 100 disks), an HP ScanJet 4890 scanner with slide and film attachments, an HP ScanJet 5300C scanner, an HP Deskjet 990Cxi printer, and a USB 2.0 thumb drive. NONE of these have worked (except the printer) since I upgraded from SuSE 9.0 to 9.2 despite repeated attempts by kind folks to help me.
4) I have a SONY DVD-RW Double layer drive and an Optorite CD-RW CW-5205 drive. The latter only works manually under SuSE 9.2.
5) I have a plusdeck 2C cassette player hooked up to my sound card. I can play cassettes manually in Linux and would like to be able to use it to convert my ancient tunes (60s and 70s) and African music to MP3s or whatever. I'll probably get a USB turntable soon and would like to do the same for my vinyl. If I don't have to re-boot into Windoze to do either of these tasks, it would be great.
6) I have to re-boot into Windoze XP to use FamilyTreeMaker genealogy software, Dragon Naturally Speaking 9 voice recognition, and occasionally Word 97 (when oOo becomes just too frustrating ...). If Ubuntu comes with an equivalent and/or can run them within Linux (using OpenOffice or VMware - which?), it would be helpful to know.
7) I have a strong ideological preference for using open source SW. Some proprietary SW is inevitable, however. How easy does Gutsy make it to download and install "outside" software?

Thanks for your assistance.  kjmorris

---

### Post by logos34 on 2007-12-02
Back up your data like you said.  Gutsy installer Migration Assistant should detect and ask to import  mail, bookmarks, OO docs, etc files, but it may not and so you'll have to restore them manually.

You don't need windows to partition the disk.  You can use Gparted on the ubuntu live cd.  

Best way to find out if your hardware is supported is to run the ubuntu live cd.  If it detects your network card, periperhals and various drives, you're in business.  

Software: you might be able to run some of those windows programs acceptably via Wine. Audacity might come in handy for some of that audio conversion. 

As for proprietary sw: if it's in a tarball, ./configure. make, make install is all there is to it.  Even easier if the vendor provides a .deb package.  Other times there's a .bin installer.  And even in cases where only an rpm is available, you can convert it using alien.

---


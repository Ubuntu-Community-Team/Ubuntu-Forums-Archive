---
title: "Ubuntu Backup Server Help"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by Kasuko on 2010-02-03
I have an old computer sans hard drive sitting around and I decided it was about time I got off my *** and started backing stuff up, my good luck can't hold forever.

The plan is to install Ubuntu on one hard drive (small IDE) and then put a RAID card in and get 2 500GB hard drives and mirror them.

I was googling and I keep getting conflicting information I can't seem to figure out. It appears theres a way to get Ubuntu on the RAID and then just getting the RAID.

Since I just want the RAID to be a seperate drive and no OS on it could I just get any of the PCI RAID Cards from [NewEgg.ca]("http://www.newegg.ca/Product/ProductList.aspx?Submit=ENE&N=2010150410%201193512552#") and then software raid them through my already installed Ubuntu?

Is this easy to set up to be notified of a failing drive? Otherwise a $200 NAS seems like a better idea but I like the thought of doing it myself.

Thanks so much for your input.
Kasuko

---

### Post by pkm4o93 on 2010-02-03
Hello RAID is not a backup.  [http://www.smallnetbuilder.com/nas/nas-basics/30060-smart-sohos-dont-do-raid](http://www.smallnetbuilder.com/nas/nas-basics/30060-smart-sohos-dont-do-raid)

---

### Post by Kasuko on 2010-02-03
Ok, constructive criticism? Best way go about implementing a back up server?

---

### Post by pirateghost on 2010-02-03
> **pkm4o93 said:**
> Hello RAID is not a backup.  [http://www.smallnetbuilder.com/nas/nas-basics/30060-smart-sohos-dont-do-raid](http://www.smallnetbuilder.com/nas/nas-basics/30060-smart-sohos-dont-do-raid)

> **Kasuko said:**
> Ok, constructive criticism? Best way go about implementing a back up server?

pkm, i too am with you in spreading the word that RAID is not backup, but i think Kasuko understands that and is instead wanting to create a server with storage on it that is in RAID and perform backups of his other machines to it.

Kasuko,
most of the cheaper cards are not real RAID cards, and yes you should be able to pick up pretty much any SYBA or even Rosewill SATA card and utilize linux raid on those drives.

get a small harddrive, install the OS on it, and begin configuring.  add the 2 storage drives after you get the bulk of the configuration done, and have a look at [http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

i cant say enough how much i love this piece of software, compression, dedup, versioning (based on your backup schedule), free, and efficient.
it uses rsync to run backups (you can run rsync on windows(deltacopy) or linux pcs(rsync), dont know about macs)

i have a similar setup on a debian box.

raid'd drives presented via iscsi to my backup machine, formatted as ext3 and mounted on /var/lib/backuppc (heres a hint: set up your raid drives and mount them before installing backuppc)

---

### Post by Kasuko on 2010-02-03
Thank you and yes that is what I was referring to. I wasn't planning on using the RAID as my backup but to use the RAID to hold the backups. I just wanted the RAID mirror so that when my backup hard drive fails I can swap out another one. Although that website did scare me. Am I to believe that if the controller hardware dies I could lose everything?

I looked up BackupPC and it looks GREAT! Just what I am looking for as I was just going to script together some rsync tasks.

Thanks for the help.

---

### Post by pirateghost on 2010-02-03
> **Kasuko said:**
> Thank you and yes that is what I was referring to. I wasn't planning on using the RAID as my backup but to use the RAID to hold the backups. I just wanted the RAID mirror so that when my backup hard drive fails I can swap out another one. Although that website did scare me. Am I to believe that if the controller hardware dies I could lose everything?

I looked up BackupPC and it looks GREAT! Just what I am looking for as I was just going to script together some rsync tasks.

Thanks for the help.
the beauty of linux raid.  you can put those drives on any controller that is recognized by linux and the raid will be seen (assuming you have mdadm installed) and you can mount it right away, data unscathed.

---

### Post by Kasuko on 2010-02-03
Ah ok, scared me. That's exactly what I want to hear. Now to scrounge up the money from my student lifestyle for more computer hardware ... MOM!!!! :P

---


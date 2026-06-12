---
title: "RAID Problem-After Installation Ubuntu Server 14.04 Show Blank Screen and can't Login"
date: 2016-01-15
forum: Installation &amp; Upgrades
---

### Post by sadegh2 on 2016-01-15
I have a home server with below specification:
> - Asus Z87-C motherboard
- 2 Internal Network Card (One On board and One PCI)
- 2 X HDD 1TB (RAID1-Mirror through motherboard solution - Not Software RAID)
- CPU Core-i7
- Ram 2 X 8 GB
I want install ubuntu server 14.04 on above server with disk  installation. At the installation process, I see two window about RAID  solution. I don't know which should be select. (Because my both HDD are  hardware RAID1(Mirror) from motherboard)
[First and second RAID dialogue box in installation process]("http://i.stack.imgur.com/OJIhr.jpg")

After this step (I try it both (yes/no) ways and result is one - Blank Screen at the end), in the partition setting, I use LVM item, (Please see below picture in final on partition step. I select Yes button).
  [URL="http://i.stack.imgur.com/u6jMy.jpg"]Final of partition step 

[/URL]

  And, installation ended without any problem. But when the system  restarted at the end of installation process, not loaded any menu, items  login page for access to ubuntu server. when the system loaded, I see  only a black and blank screen with a spacer. (And I can't type any  thing). After installation I tried to remove RAID from motherboard setting, I  was surprised. The issue was resolved (Without motherboard/hardware  RAID). But I want RAID1 (Mirror) in this server. Could you help me?

---


---
title: "Xubuntu install script problem"
date: 2006-04-28
forum: Installation &amp; Upgrades
---

### Post by coze on 2006-04-28
Hi there everyone,
I've been using ubuntu for about a week now and I'm so pleased with it I decided to change my lightweight linux from dsl to xubuntu. I downloaded the live cd and booted it with no problems. I liked what I saw so I wanted to install to my hd but after the install script formats the partitions, it just terminates. no files copied, nothing done.

here's some infromation about my setup. The pc is a panasonic notebook with pen-M processor, 512mb of ram. Hd has 3 primary 2 logical partitions, I'm trying to install xubuntu into a 3gb primary partition, set swap as a 4gb logical partition (sharing with ubuntu and gentoo). Since my hd is already partitioned, I make no changes to the partition table in the install script (just mark the root and swap partitions).

having said all that, I wonder if there's a possibilty to install this manually without the script. just copy the files from the cd, change some files, and give some parameter to the grub (initrd) (grub is already installed, with ubuntu).

would appreciate any comments. thanks to all the devs & people who participated in this great product.:)

---

### Post by Kapre on 2006-04-28
[QUOTE=coze]Hi there everyone,
I've been using ubuntu for about a week now and I'm so pleased with it I decided to change my lightweight linux from dsl to xubuntu. I downloaded the live cd and booted it with no problems. **I liked what I saw so I wanted to install to my hd but after the install script formats the partitions, it just terminates. no files copied, nothing done.**[/quote]

Did you get the install cd? If you're trying to install from a LiveCD, you can not do it. Get your install CD, then install "server". Then follow this [link]("http://doc.gwos.org/index.php/Minimal_Install").

---


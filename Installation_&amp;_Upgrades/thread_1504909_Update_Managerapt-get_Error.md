---
title: "Update Manager/apt-get Error"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by maniacss on 2010-06-08
Hello. I've just recently installed Ubuntu 10.04 two hours ago, on my second hard drive partition. Everything was working good until I got this error while trying to update.

'E:Type &#8216;get&#8217; is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Also when I try to download and install files using "sudo apt-get" command in terminal the same error appears. I'm new to Ubuntu so I have no idea even how to begin fixing this. I would greatly appreciate any help. Thank you.

---

### Post by bod720 on 2010-06-08
What exactly are you trying to install and what is the exact code you are putting in?

---

### Post by Jeroensum on 2010-06-08
Please dump the output of this terminal command:

cat /etc/apt/sources.list

I think there might be an error in the sources.list file somewhere around line 54 ;)

---


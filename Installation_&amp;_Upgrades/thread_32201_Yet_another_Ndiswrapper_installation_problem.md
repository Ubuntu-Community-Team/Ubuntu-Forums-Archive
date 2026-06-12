---
title: "Yet another Ndiswrapper installation problem"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by Kino on 2005-05-06
Hi everybody, 

Please be patient with another newbie and another Ndiswrapper-Wireles issue.

_ ** Right now I don’t have Internet access **_ and therefore I can’t use synaptic or apt-get when I’m running Ubuntu, almost all the solutions in the forums/howto[COLOR=Red]** presume that you are connected**[/COLOR]. I can download a file in my Windows partition and move the file to the Ubuntu partition.

I was enjoying my wireless access using a USB Dongle in Ubuntu 4.10 Warty, I got some binary debian packages which worked pretty well. But then I upgraded ](*,)  ] to 5.04 Hoary, and now the same ndiswrapper binary doesn´t work. I think they are supposed to be used with kernel 2.6.8 and Hoary uses kernel 2.6.10. I tried to find more updated binary package without success. 

In the whole process I learnt a lot, but I still have some doubts:

1. Isn’t Ndiswrapper binaries in the Ubuntu CD?, Is it possible to install packages  coming in the Ubuntu install CD?. This would solve my problems.

2. Is it possible to download the binaries packages from the Ubuntu repositories (web page: [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu)) instead of using synaptic, and later installing the package manually with dpkh -i?. 

3. If it isn’t possible to get a binary package, I would need to compile, but then again I’d  need the kernel headers which I can’t get. Am I right?

What do you recommend to have ndiswrapper running in my Ubuntu 5.04?. I think it takes a lot of effort to successfully run your linux machine, fortunately there is the community helping you.

Thank you for your help.

---

### Post by Shaggy on 2005-05-06
As far as I remember yes the ndiswrapper package is on the cdrom.  So all you would have to do is use synaptic to install the package.  Just make sure that the cd is on the repository list.

That should take care of 2 and 3 on your list.

---


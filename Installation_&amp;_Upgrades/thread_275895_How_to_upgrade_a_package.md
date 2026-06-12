---
title: "How to upgrade a package"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by lachesis on 2006-10-12
I have installed Ubuntu 6.06. Unfortunately the installed version of XSane doesn't work with my scanner. I tried out Ubuntu 6.10 and that version of XSane 0.99.1 worked fine.

I would prefer, for the moment, to use Ubuntu 6.06 but unfortunately I can't figure out how to upgrade just XSane. I looked in Synaptic and did a search but all I can see is that XSane is installed. I can't see where to upgrade it.

Thanks for your help. Sorry if it's a really obvious answer. (If it helpds I still have the 6.10 install cd. I put that in the drive and it added to the repository list in Synaptic. However, when I do a search for xsane it still shows version 0.97 and when I right click, mark for upgrade it greyed out.)

---

### Post by angkor on 2006-10-12
You probably don't want to add the 6.10 cdrom to your sources.list because you will be prompted to upgrade a _lot_ of apps everytime you run a package manager.

You could try to copy the Xsane deb from the cd to your home and install it manually with gdebi (double-click the .deb in your file manager).

If the dependencies are the same for the newer version everything should work fine, but since I haven't done it myself I don't know for sure.

You can also download single edgy .debs from here:

[http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)

Did you by the way 'reload' your repository list in Synaptic or run 'sudo apt-get update' after you added the cdrom? You will need to do that everytime you change your sources.list to make the new packages available.

---

### Post by lachesis on 2006-10-14
Thanks for your reply.

I wasn't able to find the .deb file for xsane on the cd (I may have searched the wrong way).

So I tried to download the package, but it seems there are a few dependancies that have changed. I got up to about 4 or 5 before I decided I might be best to wait a couple of weeks or so for the next release :)

Regarding adding the cd to the repository, I'm pretty sure I did Reload after it, but maybe not. However, I've removed it because it makes sense that I don't want to be offered all these upgrades when I run synaptic.

All in all I think I'll be best to wait for Edgy - I know it would be worthwhile learning how to do what I want, but I'll wait til I have a bit more knowledge under my belt.

---

### Post by hw-tph on 2006-10-14
You can download the sources and build the latest version of xsane and install the built program as usual ("make install") instead of using the .deb that depends on Edgy package versions. Use **sudo apt-get build-dep xsane** to make sure you have all the development packages you need to compile xsane from source.


Håkan

---

### Post by lachesis on 2006-10-14
Do I need to add any particular sources in order to do this? At the moment I am back to the default ones for Dapper.

If I understand you correctly, assuming I have the required soruces, I need to do 2 things:

1) Run sudo apt-get build-dep xsane
2) Build the latest version of xsane and install the built program

Does step 1 download the source and the source of all the dependancies? Or does it download built dependancies?

Is there a link to how I do step 2? I assume step one downloads a bunch of packages. Do I need to know where, or use particular commands to build and install the program?

Thanks again.

---

### Post by hw-tph on 2006-10-15
Step one downloads the libraries, programs and header files needed to compile xsane from source. However, it does not download the sources for the actual program you want to build. Get them from the website instead.

For step two there are lots of forum posts (howtos) and probably some entries in the wiki. It is usually not that hard - unpack, configure, make and last make install.


Håkan

---

### Post by lachesis on 2006-10-15
Great, thank you again.

I hope you don't mind, but I probably will still wait for Edgy in regards to xsane. However, I will certainly keep your help for future reference.

---


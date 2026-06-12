---
title: "Offline update problems"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by freddyandrews on 2008-08-02
Hi Guys

    I recently converted my 12 year old cousin to Ubuntu. Now here comes the hard part. She don't have an internet connection. So I carried all .deb packages from my /var/cache/apt/archives to the offline machine and installed it all with "dpkg -i * .deb" hoping to replicate what ever I had on my machine and to update the os. All packages were not installed properly as I expected since our hardware was different. 

    Now the problem is when I go to the synaptic I see a lot of red boxes mentioning not properly installed. When I try to remove those packages I see a lot more packages being marked for removal including "ubuntu-desktop" and god knows what else. 

    Is there a way to clean up the synaptic? or remove the packages which were not properly installed?

Any help is welcome. Thanks in advance guys.

---

### Post by coffeecat on 2008-08-02
I don't think the difference in hardware was the problem. The hardware is irrelevant to most of the packages. I think that using dpkg was the problem. This would have installed all the deb packages regardless. If you had tried with apt-get it wouldn't have installed anything (probably) because it wouldn't have had the latest package metadata. Some (most) of the packages you transferred will be later versions than Synaptic knows about (not having the metadata), so it's got in a muddle and wants to remove things.

Normally, you get the latest metadata when you click on the 'Reload' button in Synaptic and, of course, you need an internet connection for this. And I don't know how you can transfer the metadata even if you could download it elsewhere.

The only thing I can suggest is to transport your cousin's machine (temporarily) to where you can connect to the internet - preferably broadband with an ethernet cable to a router for minimal hassle. Open Synaptic and click on Reload, and then see what it has to say. You may have to 'Fix Broken Packages' from the Edit menu and, for good measure, you might as well check to see if there are any further updates to apply.

---


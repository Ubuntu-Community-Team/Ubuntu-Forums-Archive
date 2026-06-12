---
title: "Microsoft WSUS like option for ubuntu? (Windows Server Update Services server)"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by rslrdx on 2008-01-30
Is there such a tool to imitates the functionality of WSUS ? (Windows Server Update Services server)

This tool/server allows you to download updates to a server, and then tell the machines on your network to use the internal server instead of the servers on the internet, but not only that, you can test it before in make available to the local network and even remove updates already installed from the local machines.

I know ubuntu updates are fast, but if i have an office with 30 machines, and only a 400Kbps connection, it could make it slow. having updates locally would be great.

I like to know if anyone has seen anything like it, or know how to create a network setup that can kinda of copy this network solution.

Thanks in advance, Rodrigo.

[http://en.wikipedia.org/wiki/Windows_Server_Update_Services]("http://en.wikipedia.org/wiki/Windows_Server_Update_Services")

---

### Post by rslrdx on 2008-02-01
anyone? anything?

---

### Post by el_txavo on 2008-03-31
> **rslrdx said:**
> anyone? anything?

Hi,

I get through your post looking for something similar to WSUS. AFAIK there's no WSUS-like solution for Ubuntu or Debian. Hope it's not to late :)

I think you could solve your problem using **apt-cacher**. The idea is installing **apt-cacher** in one of your computers (this would be a server which will retrieve the packages from the Internet) and configure the rest to have it as their repository. The server will only download the packages asked by the other computers, so there will be no need to download the entire repository.

If you have space enough you could install **apt-mirror** to set up a mirror of the repository which you usually install packages from. With this solution the mirror would be updated regularly to match the packages available in the repositories.

An intermediate solution would be **apt-proxy** or **approx** (I think approx developement is more active), which build a mirror of the repositories based on the requests made by the computers when installing packages.

Not sure of which one best suits your needs...

---

### Post by PanzerMKZ on 2008-03-31
The apt-mirror stuff has worked great for me.  but I am going to see if I can't control internal dns so that on a box that does not normally live in my network will still get the updates locally and I don't have to change apt-get.conf all the time.



Panzer

---


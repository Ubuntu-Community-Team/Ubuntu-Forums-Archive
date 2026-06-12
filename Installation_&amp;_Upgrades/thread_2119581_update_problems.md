---
title: "update problems"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by rexmundi243 on 2013-02-24
I recently installed ubuntu 64bit on my HP probook 6465b
It is in dual boot mode with windows7, and the ubuntu installation appears to have caused a minor conflict in windows, but nothing that bothers me, I mention it in case it is important.

When I first installed ubuntu on it three days ago, I think that then it went and got the latest updates no problem.

I then installed mesa-utils, which then recognised my graphics system, so I thought all was finished and running well.

I then spent the past two days working on two other machines, installing ubuntu 32 bit on them, and now they are running well, it is back to this one, my main machine.

Yesterday evening I fired it up, and it found that 43 updates were available, so I clicked for it to go ahead as normal.

It failed, giving me the message:

Update manager
Failed to download package files
check your internet connection

My internet connection is fine, it is both cabled and wifi, both active and connected fine, I'm typing in this forum now as evidence...
I left it till today, and again exactly the same thing has happened.

System details:
OS: Ubuntu 12.04LTS
Memory: 15.2GiB
Processor: AMD A6-3430MX APU with Radeon(tm) HD Graphics × 4 
Graphics: VESA SUMO
OS Type: 64 bit

problem:
43 updates available

Update manager
Failed to download package files
check your internet connection
details:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_18.0.2+build1-0ubuntu0.12.04.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_18.0.2+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-image-generic-lts-quantal_3.5.0.24.31_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-image-generic-lts-quantal_3.5.0.24.31_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-headers-generic-lts-quantal_3.5.0.24.31_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-headers-generic-lts-quantal_3.5.0.24.31_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-generic-lts-quantal_3.5.0.24.31_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-generic-lts-quantal_3.5.0.24.31_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-38_3.2.0-38.60_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-38_3.2.0-38.60_all.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-38-generic_3.2.0-38.60_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-38-generic_3.2.0-38.60_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.2.0-38.60_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.2.0-38.60_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-signed-image-generic-lts-quantal_3.5.0.24.31_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-signed-image-generic-lts-quantal_3.5.0.24.31_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-signed-generic-lts-quantal_3.5.0.24.31_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-quantal/linux-signed-generic-lts-quantal_3.5.0.24.31_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]

Any help would be appreciated

I eventually intend to get rid of the windows OS for good, if I can see this laptop running ubuntu well... and so far I am more than happy with it.... the other two machines I have just sorted are solely ubuntu now

Rex

---

### Post by matt_symes on 2013-02-24
Hi

Try a different server for your updates. You can do this from update-manager if i remember correctly.

Kind regards

---

### Post by rexmundi243 on 2013-02-24
I set the software sources for UK and tried again, same result, it started downloading then failed, the same as before.

I may have to try a total reinstall of ubuntu.

---

### Post by matt_symes on 2013-02-24
Hi 

Look at the links ypou posted in a browser. You will see that don't actually exist at the moment. 

That is why they can't be found because they don't exist. 

They may be temporary down but they may have gone for good. You may want to remove them.

Kind regards

---

### Post by rexmundi243 on 2013-02-24
thanks for that matt...
but that just adds to my confusion....
why is ubuntu saying these updates are available, and some are supposed to be essential, I even tried only downloading the essential ones but same result.

And you say I should remove them? How? I didn't get them, it failed to download.

Does that mean I should ignore updates from now on?

What is more confusing, why does it even offer these updates if they don't even exist, and why does ubuntu insist the fault is with my connection, when it should be saying the files don't exist?
edit:
out of the 43 updates available, I even tried just selecting the first on on the list only, and it failed to do that, same results.

very confusing...

---

### Post by matt_symes on 2013-02-24
Hi

> **rexmundi243 said:**
> thanks for that matt...
but that just adds to my confusion....
why is ubuntu saying these updates are available, and some are supposed to be essential, I even tried only downloading the essential ones but same result.

And you say I should remove them? How? I didn't get them, it failed to download.

Does that mean I should ignore updates from now on?

What is more confusing, why does it even offer these updates if they don't even exist, and why does ubuntu insist the fault is with my connection, when it should be saying the files don't exist?

very confusing...

It is a condrum. 

I can only assume there is a configuration problem on the server and the package information has been updated after the packages.

Try this to remove the problem

```
sudo rm -vf /var/lib/apt/lists/*
```

Then

```
sudo apt-get update
```

Kind regards

---

### Post by rexmundi243 on 2013-02-24
Thanks Matt, that seems to have done something, perhaps most of them...

but I see it still failed on some things, the last part of my terminal message is as follows:

Fetched 19.8 MB in 1min 15s (262 kB/s)                                         
W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

Can you help me to understand that?
What does "failed to fetch cd rom" mean?
Is it looking on a cd?
edit: There is no cd in the player.

---

### Post by matt_symes on 2013-02-24
Hi

It's looking for updates in a cdrom but the cd rom is not in the drive so it spits out those messages. It's not a major issue.

Open a terminal and type

```
sudo sed -i  's/deb cdrom/#deb cdrom/g' /etc/apt/sources.list
```

That will comment it out.

Kind regards

---

### Post by rexmundi243 on 2013-02-24
Matt, I put my original ubuntu install cd in the drive and did that update on the terminal again, and got the same problem as in my above post, so it wasn't as I assumed, looking on the cd....
more confused...
Rex
edit 

ah, I see your above post arrived as I was typing mine...
I will try that

---

### Post by rexmundi243 on 2013-02-24
Done that Matt, then did sudo apt-get update, and it now has a long list that ends with:
Reading package lists... Done

do I now install, or should I add that to the above command?

---

### Post by matt_symes on 2013-02-24
Hi

> **rexmundi243 said:**
> Done that Matt, then did sudo apt-get update, and it now has a long list that ends with:
Reading package lists... Done

do I now install, or should I add that to the above command?

Well i think were pretty much done as that looks good. Do you have any other problems ?

Kind regards

---

### Post by rexmundi243 on 2013-02-24
I think all is okay now Matt, thank you very much, I am just letting update manager deal with things now ( I am now on a different machine while it does that} and so far all looks well.

---


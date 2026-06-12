---
title: "Nvidia Graphics HELP!"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by KaisaUbun2 on 2012-11-30
I currently believe that I have Nvidia driver installed. It has been sort of hard because I have the graphics with the optimus technology and so i've been having to use bumblebee. but supposedly nvidia was going to come out with a new driver so I was trying to install and update so I did as follows: 

```
sudo apt-get install nvidia-current
```

simple enough right? but then I got this response, I'm no expert so I don't know if I messed up or what this really even means. I have an idea... but I'm not absolutely positive. 

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Can anybody help me decipher this?

---

### Post by sudodus on 2012-11-30
I get this error message, if I have another installation program open, for example ***Synaptic***. If this is the case, close that program and try again.

---

### Post by kc1di on 2012-11-30
Hi KaisaUbun2,

run the following commands in a terminal and see if you can then install. 

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by KaisaUbun2 on 2012-11-30
> **sudodus said:**
> I get this error message, if I have another installation program open, for example ***Synaptic***. If this is the case, close that program and try again.

Yeap, completely forgot I was running updates in the background, and had the synaptic manager open so the Updates weren't going either. Thanks, I did not know those bar each other. 

Everyday is an opportunity to learn. However, I will not mark this as solved till the updates conclude and I get a chance to run the Nvidia command again. However, thank you ahead of time.

---

### Post by Rockfreak101 on 2012-11-30
I was having a similar problem. I used "additional drivers" to find the proper drivers for my Nvidia Geforce 650M. Once I did so, I received an error message stating it wasn't installed successfully. When I rebooted my computer my desktop border/start menu has completely disappeared. I used this tactic to ensure I have the proper drivers, but I still have not gotten my border/start menu back. 

What can I do?

---

### Post by KaisaUbun2 on 2012-11-30
I wonder though... can I install things simultaneously on separate virtual desktops?

---

### Post by KaisaUbun2 on 2012-11-30
> **Rockfreak101 said:**
> I was having a similar problem. I used "additional drivers" to find the proper drivers for my Nvidia Geforce 650M. Once I did so, I received an error message stating it wasn't installed successfully. When I rebooted my computer my desktop border/start menu has completely disappeared. I used this tactic to ensure I have the proper drivers, but I still have not gotten my border/start menu back. 

What can I do?

I wouldn't use the additional drivers thing. While it is a nice addition it lacks in ability. I'd re-install the Nvidia drivers.

---

### Post by Rockfreak101 on 2012-11-30
I did. I followed the suggestion above, and I'm still having the same issue.

I realize I shouldn't have used "additional drivers" after it was too late.

---

### Post by KaisaUbun2 on 2012-11-30
> **Rockfreak101 said:**
> I was having a similar problem. I used "additional drivers" to find the proper drivers for my Nvidia Geforce 650M. Once I did so, I received an error message stating it wasn't installed successfully. When I rebooted my computer my desktop border/start menu has completely disappeared. I used this tactic to ensure I have the proper drivers, but I still have not gotten my border/start menu back. 

What can I do?

uhm do this 

```
sudo apt-get install --reinstall nvidia-current nvidia-settings nvidia-common
```

then run 

```
apt-cache policy nvidia-current nvidia-common nvidia-settings
```

post the output, if it comes back something like this 

```
nvidia-current:
  Installed: 302.17-0ubuntu1~precise~xup1
nvidia-common:
  Installed: 1:0.2.44
nvidia-settings:
  Installed: 302.17-0ubuntu1~precise~xup3
```

I don't think your problem is with the driver

Unless you haven't installed bumblebee. I am assuming the 650 runs optimus as well?

---

### Post by Rockfreak101 on 2012-11-30
Here is what I get. (I'm sorry its so long)
nvidia-current:
  Installed: 304.51.really.304.43-0ubuntu1
  Candidate: 304.51.really.304.43-0ubuntu1
  Version table:
 *** 304.51.really.304.43-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status
nvidia-common:
  Installed: 1:0.2.71.1
  Candidate: 1:0.2.71.1
  Version table:
 *** 1:0.2.71.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     1:0.2.71 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages
nvidia-settings:
  Installed: 304.51-0ubuntu2
  Candidate: 304.51-0ubuntu2
  Version table:
 *** 304.51-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status

So it looks like its not the drivers. I will continue searching the forums. . .

---

### Post by KaisaUbun2 on 2012-11-30
> **Rockfreak101 said:**
> Here is what I get. (I'm sorry its so long)
nvidia-current:
  Installed: 304.51.really.304.43-0ubuntu1
  Candidate: 304.51.really.304.43-0ubuntu1
  Version table:
 *** 304.51.really.304.43-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status
nvidia-common:
  Installed: 1:0.2.71.1
  Candidate: 1:0.2.71.1
  Version table:
 *** 1:0.2.71.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     1:0.2.71 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages
nvidia-settings:
  Installed: 304.51-0ubuntu2
  Candidate: 304.51-0ubuntu2
  Version table:
 *** 304.51-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status

So it looks like its not the drivers. I will continue searching the forums. . .

Yeah that looks good, so it's not the Nvidia Drivers. generally even without bumblebee or ironhide this should work. You might just want to check your appearance settings, sometimes it's just a small detail that you may have changed by accident. Happens to me all the time.

---


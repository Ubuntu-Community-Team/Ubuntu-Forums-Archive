---
title: "Trouble re-installing acroread in 10.04"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by Kalirren on 2011-02-12
I'm having trouble updating Adobe Acrobat Reader (acroread) in 10.04, so I removed it and attempted to reinstall it.  Now it's telling me there are unmet dependencies.

When I run sudo apt-get install acroread, I get the following message:

> 
dypoon@home-desktop:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acroread: Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not installable
            Depends: libssl0.9.8 (>= 0.9.8m-1) but 0.9.8k-7ubuntu8.5 is to be installed
E: Broken packages
However, I've also tried running sudo apt-get build-dep acroread and this is what happened:

> 
dypoon@home-desktop:~$ sudo apt-get build-dep acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
In addition, the Ubuntu Software Center doesn't seem to think acroread is installed, but when I try to install it I get this error:
> 
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details:
acroread
I'm very confused.  Help?

---

### Post by sikander3786 on 2011-02-12
Welcome to the forums :-)

Try using aptitude.

```
sudo aptitude install acroread
```

---

### Post by Kalirren on 2011-02-12
Thank you!  I ran aptitude as you suggested:

> 
dypoon@home-desktop:~$ sudo aptitude install acroread
[sudo] password for dypoon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  acroread 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 63.4MB of archives. After unpacking 152MB will be used.
The following packages have unmet dependencies:
  acroread: Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) which is a virtual package.
            Depends: libssl0.9.8 (>= 0.9.8m-1) but 0.9.8k-7ubuntu8.5 is installed.
The following actions will resolve these dependencies:

Install the following packages:
acroread [9.4.1-1lucid1 (lucid)]

Score is -9920

Accept this solution? [Y/n/q/?] Y
The following NEW packages will be installed:
  acroread 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 63.4MB of archives. After unpacking 152MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner acroread 9.4.1-1lucid1 [63.4MB]
and it is proceeding to install.

Do you think it will continue to give me the "erroneous" behavior that I was trying to avoid, where in Update Manager I cannot click to upgrade it?

Edit:  Yeah, the greyed-out box in Update Manager is back again.  Should I not be worried about it?  can I make it go away?

---

### Post by sikander3786 on 2011-02-12
I hope everything will be just fine afterwards.

Good Luck!

---


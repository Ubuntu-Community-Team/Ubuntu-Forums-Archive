---
title: "Ubuntu Kernel version upgrade procedure."
date: 2021-09-14
forum: Installation &amp; Upgrades
---

### Post by akshay-shar on 2021-09-14
Hi, 

Query 1:

When I installed ubuntu LTS version 18.04.3, I could see kernel version as 4.15.0-144-generic, but as mentioned kernel for 18.04.3 is 5.3.
When I installed ubuntu LTS version 18.04.5, I could see kernel version as 4.15.0-122-generic, but as mentioned in official site Kernel version for 18.04.5 is 5.4.

Question: why Ubuntu 18.04.5 or .3 is coming up with 4.15 version, instead of official kernel?

Query 2:
During HWE kernel release, say for ex 18.04.3 which will have a support for 6months, during that time span if any security fix goes in? the version would be 4.15.0-x+1?
During next HEW release which will change in kernel version 4.15.0-x-y x or y? 

Query 3:
Say, I'm in 18.04.3 with kernel version as 4.15.0-144-generic, if I want to upgrade to any other path on the fly. How can we do it? where all those release security/patch kernel version maintained?

Query 4:
Say, I'm in 18.04.3 with kernel version as 4.15.0-144-generic, If I upgrade kernel version(HEW) using apt command line tool (sudo apt-get --install-recommends linux generic hwe-18.04), it is upgrade to latest 5.4.xx.xx. So what is the difference in upgrading kernel or move to 18.04.5 ? Because 18.04.5 has a 5.4 kernel version. 

Query 5:
What is the difference between dist-upgrade and apt-get --install-recommends linux generic hwe-18.04?

---

### Post by ActionParsnip on 2021-09-14
If the system is running OK and all hardware is working then I wouldn't worry about the kernel. Stop chasing version numbers unnecessarily and you'll have less worry.

---

### Post by Impavidus on 2021-09-14
1: Every LTS release of Ubuntu comes with 2 kernel lines: the standard kernel and the HWE kernel. You can switch from one to the other, if you like, and both are supported for the full support period of the release. The standard kernel remains at the same version throughout its life. For 18.04, that's 4.15.0, for 20.04 it's 5.4.0. The HWE kernel is upgraded 4 times in 6 month intervals, to the kernels used by the following Ubuntu releases. The HWE kernel for Ubuntu 18.04 is now 5.4, which is also the standard kernel for 20.04, and the HWE kernel for 20.04 is now 5.11, which is also the kernel for 21.04. Whether you get the standard or HWE kernel by default, depends on the live disk you used for installation. When you install regular upgrades, the version number of your Ubuntu system may increase from 18.04.2 to 18.04.3 etc., but that does not mean you switch from the standard kernel to the HWE kernel or back. Both kernels are official.

2: When you get a security fix to kernel 4.15.0-155, you'll get kernel 4.15.0-156. Or -157 or -158, as sometimes some numbers get skipped.

3: To switch between the standard kernel and the HWE kernel, you can install the appropriate metapackage. For 18.04, that's **linux-generic** for the standard kernel or **linux-generic-hwe-18.04** for the HWE kernel. Unless you don't want the generic kernel. Ubuntu Studio uses the lowlatency kernel. Reboot into the kernel you want, then you can remove the other.

4: As explained above, 18.04.5 doesn't have one specific kernel; it has two.

5: The apt-get dist-upgrade will install patches for the currently installed kernel line (and for all other packages), the other command is to switch from the 4.15 to the 5.4 kernel line. Note that some dashes from your command are missing.

---

### Post by akshay-shar on 2021-09-14
Thanks for replying.

Query:1 
what is the difference between standard kernel and HWE kernel? 

Query:2 
If I'm in 18.04.3 right now, and  have some security vulnerabilities with the existing kernel(4.15.0-122-generic). what should we upgrade to 18.04.4/5 or should we just upgrade HWE kernel(5.4.0-133-generic or say that security issue may fixed in 4.15.0-133-genric?
what should be difference, as ubuntu 18.04.4 may have all those issue already fixed?

---

### Post by Impavidus on 2021-09-14
1: The standard kernel on Ubuntu 18.04 is 4.15, the HWE kernel is 5.4. The difference is that 5.4 is newer. It has better support for more recent hardware, but also has more bugs. Your choice. Both kernels get regular bugfixes, in particular security fixes, but no support for new hardware. And if you've got recent hardware, don't run 18.04. Use 20.04 instead.

2: If you're affected by a bug in 4.15.0-122, just install the regular upgrades waiting for you. That will install kernel 4.15.0-156. Actually, install that upgrade anyway, along with all other available upgrades, even if you're not aware of any problems that could be solved by this. The idea behind (semi-)automatic upgrades is that you don't have to worry about them. It works very well, 99.99% of the time.

Actually, if your system tells you you're at 18.04.3, there must be upgrades waiting or something is really wrong. The version number should have incremented to 18.04.4 in January 2020 and to 18.04.5 in July 2020. This version number doesn't mean a lot, but it does tell that the package containing the version number is at the stage it had somewhere between July 2019 and January 2020.

There's no such thing as upgrading to 18.04.4. 18.04.3 is 18.04 with all upgrades released until July 2019, 18.04.4 is 18.04 with all upgrades released until January 2020 and 18.04.5 is 18.04 with all upgrades released until July 2020.

---

### Post by grahammechanical on 2021-09-14
> What is the difference between dist-upgrade and apt-get --install-recommends linux generic hwe-18.04?

I quote what the man (manual) page for apt-get says about "dist-upgrade:"

> dist-upgrade
            dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages [COLOR=#ff0000]at the expense of less important ones if necessary[/COLOR]. The dist-upgrade [COLOR=#ff0000]command may therefore remove some packages.[/COLOR] The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages. 

Regards

---

### Post by MAFoElffen on 2021-09-14
Well... LOL.

I quite and easy thing for you do do would to verify if you are actually HWE or not for your release version...
```

uname -r
apt-cache show linux-generic-hwe-$(lsb_release -sr) | awk '/Depends:/ {print $2 ", Kernel Version = " $4}' | sed 's/..$//'
sudo apt list | grep linux-generic-hwe-$(lsb_release -sr)

```
- The first will show which kernel you are running on currently.
- The second will show you which kernel you should be running on if your were in an HWE series for your release.
- The third will show output if you have HWE installed for your release, or be blank if not installed.

---

### Post by akshay-shar on 2021-09-15
thank you all. 

It pretty much answer all my doubts, just one more small query.

1) when we ran apt-get dist-upgrade, we could see point release 18.04.3 upgrade to 18.04.4/5 but kernel (uname -r) was same only. why it is so? kernel should also update right?


2) From 18.04.3, we do just apt-get upgrade we would get all latest package and bug fixes? or we need to go to 18.04.4/5 to have latest bug fixes after jan 2020?

---

### Post by akshay-shar on 2021-09-15
query 1: HWE kernel I know how to upgrade, but how to upgrade Standard release kernel(4.15)? 

query 2: IF I'm in 18.04.3, and I want all latest security fixes and bug fixes, Should I move to latest point release or can get all bug fix on current release by upgrading Kernel.?

---

### Post by deadflowr on 2021-09-15
Have you rebooted yet?
Kernel updates require a reboot in order to load the new kernel.

> we do just apt-get upgrade we would get all latest package and bug fixes?
No.
apt-get upgrade is the weakest (or some say safest) apt-get command as it only updates packages already installed,
but some updates will require installing new packages.
Chances are at some point when running apt-get upgrade it'll state that some packages will have be to be held back.

For full updates run the dist-upgrade command, or run apt commands such as 
```
sudo apt full-upgrade
```
Those commands will install new packages when the update requires it.

---

### Post by akshay-shar on 2021-09-15
> **MAFoElffen said:**
> Well... LOL.

I quite and easy thing for you do do would to verify if you are actually HWE or not for your release version...
```

uname -r
apt-cache show linux-generic-hwe-$(lsb_release -sr) | awk '/Depends:/ {print $2 ", Kernel Version = " $4}' | sed 's/..$//'
sudo apt list | grep linux-generic-hwe-$(lsb_release -sr)

```
- The first will show which kernel you are running on currently.
- The second will show you which kernel you should be running on if your were in an HWE series for your release.
- The third will show output if you have HWE installed for your release, or be blank if not installed.


uname -a 
Linux ubuntu 4.15.0-156-generic #163-Ubuntu SMP Thu Aug 19 23:31:58 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

apt-cache show linux-generic-hwe-$(lsb_release -sr) | awk '/Depends:/ {print $2 ", Kernel Version = " $4}' | sed 's/..$//'
linux-image-generic-hwe-18.04, Kernel Version = 5.4.0.84.94~18.04.75

sudo apt list | grep linux-generic-hwe-$(lsb_release -sr)
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


linux-generic-hwe-18.04/bionic-updates,bionic-security 5.4.0.84.94~18.04.75 amd64
linux-generic-hwe-18.04-edge/bionic-updates,bionic-security 5.4.0.84.94~18.04.75 amd64

so, as per your comments, I could see 4.15.0-156 is currently running and according  to apt list "hwe 5.4.0.84 is installed", how is this possible?

---

### Post by deadflowr on 2021-09-15
It doesn't say anything about 5.4.0-84 being installed.
The command only lists what current kernel would be available, not which are installed.

It would mark which are installed clearly like this
```
linux-generic-hwe-18.04/bionic-updates,bionic-security,now 5.4.0.84.94~18.04.75 amd64 [installed]
linux-generic-hwe-18.04-edge/bionic-updates,bionic-security 5.4.0.84.94~18.04.75 amd64

```

See the [installed] marker.

You can see what you have by cutting down the command to just

```
apt list | grep linux-generic
```
It should show the 4.15.0-156-generic listed with the [installed] mark.

---

### Post by akshay-shar on 2021-09-15
[COLOR=#000000]query 1: HWE kernel I know how to upgrade, but how to upgrade Standard release kernel(4.15)? say, 18.04.3 is coming up with kernel 4.15.0-122-generic and I want to upgrade to latest/stable 4.15.XX.XX GA version or how to upgrade to specific kernel version? for ex 4.15.0-144-generic[/COLOR]

[COLOR=#000000]query 2: IF I'm in 18.04.3, and I want all latest security fixes and bug fixes, Should I move to latest point release or can get all bug fix on current release by upgrading Kernel.?


[/COLOR]

---

### Post by Impavidus on 2021-09-15
1: As explained in post #3, nothing special to do. Just install the upgrades waiting for you:```
sudo apt-get update
sudo apt-get dist-upgrade
```or some variation on that. If you really want some specific kernel instead of the latest, that can be done, but why would you?

2: As explained in post #5, there is no such thing as upgrading to a point release. If you just install the available upgrades, at some point the version number is incremented (it's in the base-files package), but that doesn't really have any meaning. Of course, the kernel isn't the only thing that gets upgrades, neither is the file that contains the version number.

---

### Post by akshay-shar on 2021-09-15
Version incremented you mean, 18.04.x ? for ex: 3 to 4 ? 
or you are referring to kernel version?

---

### Post by Impavidus on 2021-09-15
I was referring to 18.04.3 to 18.04.4, but kernel versions also increase occasionally when you regularly install your upgrades. They are completely unrelated, but both happen as a result of installing upgrades. You could upgrade the kernel but not the 18.04.x version number, or the other way around, by would you?

Don't overthink it. I never think about upgrades, I just install them every day. All of them. That they are made available in the repositories is enough for me to feel safe installing them. It works 99.99% of the time and on the few occasions when it doesn't work, I fix it.

---


---
title: "Installed two 22.04 LTS but they are somewhat different"
date: 2023-12-22
forum: Installation &amp; Upgrades
---

### Post by seccon2 on 2023-12-22
I run two Ubuntu LTS Servers in my SoHo and I use the to host a few things like Zabbix, WebApps and similar things.

Recently I cleaned out a few apps I was not needing, when I noticed that the kernel of these servers is different. That seems very strange since they are both virtual machines hosted on the same physical server and have been installed from the same image at roughly the same time.

When I log on in SSH I see two different "welcome" messages.

Server1
> Welcome to Ubuntu 22.04.3 LTS **(GNU/Linux 6.2.0-39-generic x86_64)**

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)


This system has been minimized by removing packages and content that are
not required on a system that users do not log into.


To restore this content, you can run the 'unminimize' command.

Server2
> Welcome to Ubuntu 22.04.3 LTS **(GNU/Linux 5.15.0-91-generic x86_64)**

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)


  System information as of Fri Dec 22 08:06:38 AM UTC 2023


  System load:  0.123046875       Processes:             137
  Usage of /:   8.8% of 97.87GB   Users logged in:       0
  Memory usage: 4%                IPv4 address for eth0: 192.168.1.13
  Swap usage:   0%


 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.


   [https://ubuntu.com/engage/secure-kubernetes-at-the-edge](https://ubuntu.com/engage/secure-kubernetes-at-the-edge)


Expanded Security Maintenance for Applications is not enabled.


0 updates can be applied immediately.


Enable ESM Apps to receive additional future security updates.
See [https://ubuntu.com/esm](https://ubuntu.com/esm) or run: sudo pro status

I did change the amount of allocated RAM and CPU cores from 8GB and 12 Cores to 16GB and 4Cores on one of them recently. Could that change affect the kernel installed if it was 12cores when installing? Another weird thing is when I run "sudo pro status" on one it gives me not found, while on the other it , correctly, gives me info about benefits with pro.

Any possible or plausible explanation for this?

Both are running in Hyper-V.

---

### Post by Paddy Landau on 2023-12-22
Somewhere along the line, you have made a change. It's possible that you enabled Ubuntu Pro on the first machine, or that you chose to upgrade your kernel there and since forgot about it.

For reference, I enabled Ubuntu Pro on two machines, and my kernels are the same as your first one.
```
$ uname --all
Linux glinda 6.2.0-39-generic #40~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Nov 16 10:53:04 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```
To find out if it's enabled, enter this command:
```
$ pro status --all
```
You can also check if Livepatch has been enabled:
```
$ canonical-livepatch status --verbose
```
If you want to know more, see the [simple tutorial]("https://ubuntu.com/pro/tutorial").

---

### Post by seccon2 on 2023-12-22
Pro is not enabled on either. 

uname --all gives on server 1
> Linux ubsvr1.lan.conram.it 6.2.0-39-generic #40~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Nov 16 10:53:04 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

uname --all gives on server 2
> Linux ubsvr2.lan.conram.it 5.15.0-91-generic #101-Ubuntu SMP Tue Nov 14 13:30:08 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Paddy Landau on 2023-12-22
> **seccon2 said:**
> Pro is not enabled on either.
Did you use the second and third commands to check?

Maybe your second machine has had a kernel upgrade, but you haven't rebooted it yet?
```
$ apt list --installed 'linux-image*'
```
As an extra check, you can confirm that you really do have 22.04 on both machines:
```
$ lsb_release --all
```
Ubuntu Pro is free of charge for up to 5 machines, so I recommend that you enable it on both machines. You'll get the upgraded kernel on the second machine; and, on both machines, [extra updates]("https://ubuntu.com/pro") that you wouldn't otherwise receive. You'll also get Livepatch to provide live kernel updates, which allows you to go longer without rebooting — in most cases, a kernel upgrade will be both installed and enacted without needing a reboot. I'm not aware of any downsides to enabling Ubuntu Pro.

---

### Post by seccon2 on 2023-12-22
I have checked pro and pro is not installed. I would have known since I only have 5 pro licenses and I have used 1 of them on a completely different machine.

```
apt list --installed 'linux-image*'
``` gives:
1
> linux-image-6.2.0-37-generic/jammy-updates,jammy-security,now 6.2.0-37.38~22.04.1 amd64 [installed,automatic]
linux-image-6.2.0-39-generic/jammy-updates,jammy-security,now 6.2.0-39.40~22.04.1 amd64 [installed,automatic]
linux-image-generic-hwe-22.04/jammy-updates,jammy-security,now 6.2.0.39.40~22.04.16 amd64 [installed]
2
> linux-image-5.15.0-89-generic/jammy-updates,jammy-security,now 5.15.0-89.99 amd64 [installed,automatic]
linux-image-5.15.0-91-generic/jammy-updates,jammy-security,now 5.15.0-91.101 amd64 [installed,automatic]
linux-image-generic/jammy-updates,jammy-security,now 5.15.0.91.88 amd64 [installed,automatic]

```
lsb_release--all
``` gives
1
> No LSB modules are available.Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy
2
> No LSB modules are available.Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy

---

### Post by Paddy Landau on 2023-12-22
Hmm… Well, I suggest installing Ubuntu Pro, which will get your machines upgraded.

I can't tell you for certain why one has an updated kernel and one still has the default, sorry.

(I'm presuming in all of this that you have run the usual updates.)

---

### Post by seccon2 on 2023-12-22
> **Paddy Landau said:**
> 
(I'm presuming in all of this that you have run the usual updates.)

Always.

ok, I will try pro... lets see if that helps.

---

### Post by Paddy Landau on 2023-12-22
I just had a thought&#8230;

Maybe you enabled Ubuntu Pro on the first machine at some time, and later you disabled it. That would explain the discrepancy.

---

### Post by seccon2 on 2023-12-22
I do no think so.

In any case, differences persist. There were two withheld upgrades that I manged to get done on Server2, but other than that, still the same.

There is a slight chance I may have used a different ISO as source for the installations, but it should still have been a 22.04 iso, so I do not see how that may have any effect.

Any way to force kernel upgrades?

---

### Post by Paddy Landau on 2023-12-22
> **seccon2 said:**
> There were two withheld upgrades that I manged to get done on Server2, but other than that, still the same.
That's might be due to [phased updates]("https://ubuntu.com/server/docs/about-apt-upgrade-and-phased-updates").
> **seccon2 said:**
> There is a slight chance I may have used a different ISO as source for the installations, but it should still have been a 22.04 iso, so I do not see how that may have any effect.
That's unlikely to have made a significant difference. Although, having said that, if machine 1 used a later ISO, it might have had a different default kernel. I vaguely remember something about that.
> **seccon2 said:**
> Any way to force kernel upgrades?
There is, but as I don't recall how, I don't want to give advice in case it breaks your machine. The best way is to use Ubuntu Pro; you have only one license in use, so you have enough slots left.

---

### Post by ActionParsnip on 2023-12-22
Sounds like you installed the HWE kernel on the one with 6.2.0-39

---

### Post by MAFoElffen on 2023-12-22
Wait... I see something I recognize from those motd's.

Please post the output of 
```

apt list ubuntu-server* --installed
apt list linux-generic* --installed

```

---

### Post by oldfred on 2023-12-22
I think you did this on the one with newer kernel. Either by setting it or installing newer point version.
Does not show 22.04, but same logic used as older versions.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://ubuntu.com/kernel/lifecycle](https://ubuntu.com/kernel/lifecycle)

to see status
hwe-support-status --verbose

Install with 22.04 or 22.04.1 uses the 5.15 kernels for stability. But any newer point version gets automatic newer kernels.
If enablement used, it upgrades kernels to newer versions to support newer systems but with LTS version.

---

### Post by seccon2 on 2023-12-23
> **MAFoElffen said:**
> Wait... I see something I recognize from those motd's.

Please post the output of 
```

apt list ubuntu-server* --installed
apt list linux-generic* --installed

```

Here goes:

Server1
```

$ apt list ubuntu-server* --installed
Listing... Done
$ ubuntu-server-minimal/jammy-updates,now 1.481.1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it
$ apt list ubuntu-server* --installed -a
Listing... Done
$ ubuntu-server-minimal/jammy-updates,now 1.481.1 amd64 [installed]
$ ubuntu-server-minimal/jammy 1.481 amd64

$ apt list linux-generic* --installed
Listing... Done
$ linux-generic-hwe-22.04/jammy-updates,jammy-security,now 6.2.0.39.40~22.04.16 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it
$ apt list linux-generic* --installed -a
Listing... Done
$ linux-generic-hwe-22.04/jammy-updates,jammy-security,now 6.2.0.39.40~22.04.16 amd64 [installed]
$ linux-generic-hwe-22.04/jammy 5.15.0.25.27 amd64

```

Server2
```

$ apt list ubuntu-server* --installed
Listing... Done
$ ubuntu-server-minimal/jammy-updates,now 1.481.1 amd64 [installed]
$ ubuntu-server/jammy-updates,now 1.481.1 amd64 [installed]

$  apt list linux-generic* --installed
Listing... Done
$ linux-generic/jammy-updates,jammy-security,now 5.15.0.91.88 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it
$  apt list linux-generic* --installed -a
Listing... Done
$ linux-generic/jammy-updates,jammy-security,now 5.15.0.91.88 amd64 [installed]
$ linux-generic/jammy 5.15.0.25.27 amd64

```


> **oldfred said:**
> I think you did this on the one with newer kernel. Either by setting it or installing newer point version.
Does not show 22.04, but same logic used as older versions.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://ubuntu.com/kernel/lifecycle](https://ubuntu.com/kernel/lifecycle)

to see status
hwe-support-status --verbose

Install with 22.04 or 22.04.1 uses the 5.15 kernels for stability. But any newer point version gets automatic newer kernels.
If enablement used, it upgrades kernels to newer versions to support newer systems but with LTS version.

HWE status as requested:

Server1
```
$ hwe-support-status --verbose
Your Hardware Enablement Stack (HWE) is supported until April 2027.

```

Server2
```
$ hwe-support-status --verbose
**You are not running a system with a Hardware Enablement Stac**k. Your system is supported until April 2027.

```

Hokay, so there is that. I will check your links in a few days, in the middle xmas stuff... :wink:


Thank you both...

---

### Post by MAFoElffen on 2023-12-23
Also note that Server 1 only has Server Minimal installed. That is why in the motd for it, it says that only a minimal installation is present... but that same server has the HWE stack kernel versions...

What I recognized from post #1:
> 
(GNU/Linux [COLOR=#ff0000]6.2.0-39-generic[/COLOR] x86_64)

[I][B][COLOR=#ff0000]This system has been minimized by removing packages and content that are
not required on a system that users do not log into.[/COLOR][/B][/I]

Server 2 is ubuntu-server (full) and has the linux-generic kernel series, without HWE...

---

### Post by seccon2 on 2023-12-24
In regards to minimized or unminimize both has been unminimized before adding them to "Pro".

Server 1
```

$ unminimize
This system has been minimized by removing packages and content that are
not required on a system that users do not log into.


This script restores content and packages that are found on a default
Ubuntu server system in order to make this system more suitable for
interactive use.


Reinstallation of packages may fail due to changes to the system
configuration, the presence of third-party packages, or for other
reasons.


This operation may take some time.


Would you like to continue? [y/N] y


Removing lxd installer package...
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'lxd-installer' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Installing lxd from snap...
snap "lxd" is already installed, see 'snap help refresh'
```

Server 2
```

$ unminimize
This system has been minimized by removing packages and content that are
not required on a system that users do not log into.


This script restores content and packages that are found on a default
Ubuntu server system in order to make this system more suitable for
interactive use.


Reinstallation of packages may fail due to changes to the system
configuration, the presence of third-party packages, or for other
reasons.


This operation may take some time.


Would you like to continue? [y/N] y


Removing lxd installer package...
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'lxd-installer' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Installing lxd from snap...
snap "lxd" is already installed, see 'snap help refresh'
```

I better just delete everything and start over. I hate inconsistencies.

---

### Post by Paddy Landau on 2023-12-24
> **seccon2 said:**
> I better just delete everything and start over. I hate inconsistencies.
That's almost certainly unnecessary. Linux is a lot hardier than a certain other OS, and it's all but certain that you can simply enable Pro on both machines to get them fully up-to-date.

---

### Post by MAFoElffen on 2023-12-24
What I meant was: Both Servers have the ubuntu-server-minimal package installed. 

Only Server 2 has ubuntu-server package installed... 

That was a checkbox difference in the installer.

[HR][/HR] 
If you want them to be exactly alike as VM guests, I do that in few different ways...

[LIST]
[*]I create VM Templates, where I create a machine, use virt-sysprep on it to make it generic... Then clone that template to deploy machines from. 
[*]I use autoinstall.yaml and cloud-init files to create machines that are installed the same type. 
[*]I use MAAS to deploy and provision machines. 
[*]I use Ansible and Terraform to deploy and provision machines. 
[/LIST]

The only time I really worry about if multiple machines are exactly alike in configurations, and such is if I am setting them up as nodes of a cluster. Other than that, it doesn't really matter much.

---

### Post by seccon2 on 2023-12-25
/delete/

---

### Post by seccon2 on 2023-12-25
> **Paddy Landau said:**
> That's almost certainly unnecessary. Linux is a lot hardier than a certain other OS, and it's all but certain that you can simply enable Pro on both machines to get them fully up-to-date.
[COLOR=#000000]I did. All that is posted in this page of the thread are after doing that.[/COLOR]

---

### Post by seccon2 on 2023-12-25
> **MAFoElffen said:**
> What I meant was: Both Servers have the ubuntu-server-minimal package installed. 

Only Server 2 has ubuntu-server package installed... 

That was a checkbox difference in the installer.

[HR][/HR] 
If you want them to be exactly alike as VM guests, I do that in few different ways...

[LIST]
[*]I create VM Templates, where I create a machine, use virt-sysprep on it to make it generic... Then clone that template to deploy machines from.
[*]I use autoinstall.yaml and cloud-init files to create machines that are installed the same type.
[*]I use MAAS to deploy and provision machines.
[*]I use Ansible and Terraform to deploy and provision machines.
[/LIST]

The only time I really worry about if multiple machines are exactly alike in configurations, and such is if I am setting them up as nodes of a cluster. Other than that, it doesn't really matter much.

I understand that. Seems for a serious prod env. Me I am just fiddling in my homelab...

---

### Post by Paddy Landau on 2023-12-25
> **seccon2 said:**
> [COLOR=#000000]I did. All that is posted in this page of the thread are after doing that.[/COLOR]
And they're not fully up-to-date? The kernel on the second machine is still version 5? This is mine:
```
$ uname --all
Linux glinda 6.2.0-39-generic #40~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Nov 16 10:53:04 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```
In that case, do as @oldfred suggested, and enable HWE on your second machine.

---

### Post by seccon2 on 2024-01-02
> **oldfred said:**
> I think you did this on the one with newer kernel. Either by setting it or installing newer point version.
Does not show 22.04, but same logic used as older versions.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://ubuntu.com/kernel/lifecycle](https://ubuntu.com/kernel/lifecycle)

to see status
hwe-support-status --verbose

Install with 22.04 or 22.04.1 uses the 5.15 kernels for stability. But any newer point version gets automatic newer kernels.
If enablement used, it upgrades kernels to newer versions to support newer systems but with LTS version.

Went with 

```
[COLOR=#333333][FONT=monospace]sudo apt install --install-recommends linux-generic-hwe-22.04 [/FONT][/COLOR]
```

Question:

> Reading package lists... DoneBuilding dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  linux-headers-6.2.0-39-generic linux-headers-generic-hwe-22.04 linux-hwe-6.2-headers-6.2.0-39
  linux-image-6.2.0-39-generic linux-image-generic-hwe-22.04 linux-modules-6.2.0-39-generic
  linux-modules-extra-6.2.0-39-generic
Suggested packages:
  fdutils linux-doc | linux-hwe-6.2-source-6.2.0 linux-hwe-6.2-tools
The following NEW packages will be installed:
  linux-generic-hwe-22.04 linux-headers-6.2.0-39-generic linux-headers-generic-hwe-22.04
  linux-hwe-6.2-headers-6.2.0-39 linux-image-6.2.0-39-generic linux-image-generic-hwe-22.04
  linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 129 MB of archives.
After this operation, 699 MB of additional disk space will be used.
Do you want to continue? [Y/n] y

Y

Reboot...

Result:

> Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-39-generic x86_64)

**Success**.

Additional cleaning

```

$ sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-5.15.0-89 linux-headers-5.15.0-89-generic linux-image-5.15.0-89-generic
  linux-modules-5.15.0-89-generic linux-modules-extra-5.15.0-89-generic
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 582 MB disk space will be freed.
Do you want to continue? [Y/n]
```

Y

Thank you kind people, I wish you all a good 2024. 

You may even see me here again. ):P

---


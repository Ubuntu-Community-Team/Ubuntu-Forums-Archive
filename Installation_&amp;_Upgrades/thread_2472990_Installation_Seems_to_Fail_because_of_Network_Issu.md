---
title: "Installation Seems to Fail because of Network Issues"
date: 2022-03-19
forum: Installation &amp; Upgrades
---

### Post by alisonbma on 2022-03-19
Problem: I have not been able to install Ubuntu 21.04 Server/Desktop on a new Alienware machine. I believe this is because of inability to connect to internet which I see when reading the installation error log / tracebacks. This inhibits certain downloads necessary by grub and python 3.6.

Questions:
1. Is there anything I need to look for on the Grub CLI (currently it only registers one internet card) and cannot be autoconfigured for ipv6; other grub "ls" CLI commands don't list anything. 
2. If my machine has both ipv4 and ipv6 cards, do I need to select for it to use one between the two? Right now I only have IPV4 details and the server does seem to successfully register it during setup but still cannot seem to use/find it?
3. Is there a driver I need to setup for Ethernet?
4. Currently the Ethernet box I connect to powers other machines / ubuntu machines successfully but doesn't connect to Internet on my MacOS. Am I missing something? The machines are generally hooked up to some remote server and maybe that is a separate Ethernet cable for remote server related processes, different from regular Internet connectivity?

Thank you for the help!

---

### Post by tea for one on 2022-03-20
Ubuntu 21.04 is now End of Life and you should try a supported release i.e. 21.10 or 22.04 (currently in development with final release date April 21st 2022).
[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)
As you have a new PC, generally you need a recent kernel.
You can install without an internet connection.

---

### Post by MAFoElffen on 2022-03-20
Do you have typo's in your title and post? If not, you are confusing me also. Let me explain so that maybe we can talk in the same terms, have a mutual understanding of each other, what is happening and what needs to be done.  

I will go into a few things, so you know a little about me... I am a certified Warranty Service Tech for Dell, HP and Lenovo. So, yes, i know the Dell Alienware line... So if you could mention the model, it would tell if it was one of two desktop models or one of two laptop models in that line. I personally know that Dell supports Ubunt running on their hardware,and that it does run on the Alienware line... 

Which Edition of Ubuntu are you trying to install? Desktop "OR" Server? Because saying Desktop/Server is like you are saying either both at the same time, or have tried both and failed. I'm trying to figure out which media you are installing from.

Let me first explain how Ubuntu Version numbering goes and what it means... Ubuntu YY.MM LTS (Long term Support) versions are numbered as even numbers, with an YY.04 suffix, and are supported for 5 years. For instance, 20.04.x was released in April (YY.04.x) of 2020 (20.MM.x), and will be supported until April 2025. Every 6 months between an LTS release, there are interim releases, that are supported for only 9 months. The current supported interim release is 21.10. If you want long term support and stability, then most people stick with  LTS Releases. The next LTS release, 22.04, gets released next month, and will be supported until 2027.  

So "which release" of Ubuntu? Because you said 21.04... If you are trying to install version 21.04, it went into end-of-support in January 2022, 3 months ago. Since it is out of support, you would get a network error in not finding any current repositories...

Next, IPv4 and IPv6 are not separate Network cards... The network cards on any Dell Alienware Computer are capable of doing both IPv4 and IPv6. 

Does your computer boot off an Ubuntu 20.04.4 LTS USB LiveCD if you select "Try"? And if it does, open a graphical terminal session and post the output of
```

ping -c 3 -4 8.8.8.8
ping -c 3 -6 8.8.8.8
ping -c 3 -4 www.google.com
ping -c 3 -6 www.google.com

```

---

### Post by alisonbma on 2022-03-20
[COLOR=#242424][FONT=&amp]I am trying to install Ubuntu from a bootable USB on AlienwareR12(Aurora).

[/FONT][/COLOR][COLOR=#242424][FONT=&amp]Installed version: Ubuntu 21.04 Desktop (no wired connection)[/FONT][/COLOR]
[COLOR=#242424][FONT=&amp]Tried versions: 18.04 (Desktop, Server), 20.04 (Desktop, Server), 21.04 (Desktop, Server), 21.10 (Server) --> only 21.04 Server can get ethernet connection but installation still fails because of network issues so I assume the ethernet isn't sensed?

For 21.04 specifically, there were also some graphic issues that when pressing Ctrl-X to start booting, could only be resolved when typing "nomodeset" in place of the three dashes in the Grub ubuntu settings.

I'm also wondering if manually configuring something with Grub's network settings will do the trick since it senses 1 card when running net_ls_cards in the Grub CLI? [/FONT][/COLOR]https://www.gnu.org/software/grub/manual/grub/html_node/Networking-commands.html

---

### Post by MAFoElffen on 2022-03-20
Try release either 20.04.4 using HWE, 21.10 (current supported interim) or 22.04 daily (still in beta, but releases end of next month), all using 'nomodeset' to boot. It has high-end NVidia RTX 30xx GPU (standard was RTX 3070), so you will have to use that kernel boot option during the install AND during the first reboot, until you install the NVidia Graphics Driver... (using 'additional drivers')

You are also 11th Gen iCore, so will have to use HWE series kernels. Your Intel Killer Network card requires Linux kernel version 5.9.10 or higher to work. Current Ubuntu 20.04.4 HWE series kernel is version 5.13. A standard/general kernel series of 20.04 LTS will not work without HWE.

The last grub menu option on the Ubuntu 20.04.4 LiveCD (UEFI) boot menu should be to Install with HWE... Edit the linux boot line of that to add 'nomodeset'...

Ubuntu 22.04 LTS will be released with Linux kernel 5.15 as it's default kernel. Intel releases it's drivers as open source through Linux kernel, so Linux kernel versions are important to you and your hardware.

NVidia has proprietary 3rd Party drivers, so has to be install after the installation is completed, after the first boot of the installed system.

---

### Post by axlt2947 on 2022-03-20
Not quite sure how or where I can get [COLOR=#000000]20.04.4 using HWE [/COLOR]to boot the machine, so I've tried to install the release Ubuntu Server 21.10 following your suggested instructions to use 'nomodeset' to boot instead. However, the last message I see on the installation page is "configuring target system bootloader", and "installing grub to target devices". And then it failed. Am I missing anything here?

Also saw on another website saying that adding the parameter [COLOR=#232629][FONT=ui-monospace]efi_no_storage_paranoia [/FONT][/COLOR]solved the problem, however could be dangerous as it may brick the system (so am very hesitant about doing so since I'm not an expert)

Update: I figured out how to boot with the 20.04.4 using HWE and tried installing both with/without entering 'nomodeset' in grub, but still got the same fail message as the previous try (installing with 21.10)
Some more additional informations: Didn't modify anything with partitioning as it's not for dual boot, and is currently booting in UEFI mode and with secure boot disabled.

---

### Post by MAFoElffen on 2022-03-22
That is just strange... As when you use "Try" on that 20.04.4 LiveCD...

-  Do you have access to the internet in the LiveCD environment, when boot  under HWE install option, nomodeset, and using the "Try" option?

- If you check the Linux Kernel version with those options, it should be Linux Kernel 5 5.11.0-33.35. Once you upgrade, it will be at Linux Kernel 5.13.0-35. If you do
```

uname -r

```
I asked you this a few posts back, and you didn't post any results of, nor mention what happened (so sort of felt ignored). It still begs to be answered: If, while in "Try" and you ping
```

ping -c 3 8.8.8.8
ping -c 3 www.google.com

```
What are the results?

If good results, can you do an
```

sudo apt update
sudo apt upgrade

```
Which will upgrade any packages in the LiveCd Environment, then try to install again(?)

If not good results, then also tell us, to go on from there.

---

### Post by ActionParsnip on 2022-03-23
I suggest trying 22.04. It is released next month and is LTS

---

### Post by MAFoElffen on 2022-03-23
I had suggested that. His hardware demands that it runs on the newer kernels.

My test machines are running great on it...
[Ubuntu Server Development Release (22.04) Daily]("https://cdimage.ubuntu.com/ubuntu-server/daily-live/current/")
[Ubuntu Desktop Development Release (22.04) Daily]("https://cdimage.ubuntu.com/daily-live/current/")

Besides, it he used try to test if the networking is really working for him and if it does or doesn't he would know then. But he does need to answer what he has tried, so far...

---


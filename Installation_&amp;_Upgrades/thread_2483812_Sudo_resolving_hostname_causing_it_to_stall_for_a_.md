---
title: "Sudo resolving hostname causing it to stall for a minute"
date: 2023-02-09
forum: Installation &amp; Upgrades
---

### Post by vendax on 2023-02-09
Hello Forum,

I am installing Ubuntu 22.04 LTS amd64 via scripts using debootstrap. So it is a manual installation, but it should be very close to the official thing since all i am doing is using debootstrap, apt install and copying some configuration files.

The problem: sudo is installed and works eventually, but a simple **sudo whoami** would cause sudo to stall for about a minute after requesting the password. It then displays a warning message although it does function:
```
sudo: unable to resolve host ubuntu-22.04: Temporary failure in name resolution
```
Apparently, sudo is requesting network access by resolving the hostname of the machine. With the default hostname and default /etc/hosts, the hostname is not translatable. I do NOT want to fix this. I want to prevent applications from resolving the hostname and/or prevent them from having any network access.

So what i want:

**sudo whoami** -> should ask for password but not do any network stuff, it should just be as if i typed `whoami` under root user, that does not do any networking either and works fine without resolvable hostname.

**sudo apt update** -> should ask for password after which apt accesses the network. This should work. Apt is a utility designed for network access, so it is allowed to access the network. Sudo should only grant root privileges to the apt command, and not do any networking itself.

Specifically, i want to create a privacy-friendly Ubuntu version that does not "phone home" as i discovered many utilities do - without asking the user for permission. I would like to have control over my computer and understand what happens. It should not do any network activity without my explicit approval. So all background network update stuff is removed, snap removed, ntpd removed and replaced with ntpdate upon startup (after user authorized this) and so on... Wireshark should remain silent until the user engages in network activity.

Anyone can help me? Thanks in advance! :)

---

### Post by TheFu on 2023-02-09
sudoers config files are network aware.  This is to allow a central sudoers file to be managed for hundreds or even thousands of systems.  I've done this where I managed the sudoer file for over 6000 workstations and servers. 

While I haven't tried this, you might try modifying the nsswitch.conf file to only have "files" listed for name resolution.  That should prevent network requests.  However, you'll want to put files, DNS and perhaps mDNS back into the nsswitch.conf fairly soon if you expect networking on the system to work.

My nsswitch.conf file has this line, the order matters in that line:
```
hosts:          files dns 
```
I think the default settings are different between servers and desktops.

---

### Post by vendax on 2023-02-09
Thank you i will look into it!

Sidequestion though: i am looking for sudo in the most basic configuration: one user that enters password to run root commands. No advanced configuration. Apparently, sudo is more of an enterprise tool that works well for managing thousands of systems. But for a privacy-conscious single user who just wants to have a desktop, it may not be the right tool?

Are there alternatives to sudo that are much simpler and do what i want, that i use as drop-in replacement? I guess all i want is a 4KB utility that asks for password and executes as root. Seems simple enough.

I've found one alternative: **doas** which seems lightweight. I am thinking of symlinking sudo to doas and create a working drop-in replacement that way. Will that work?

---

### Post by TheFu on 2023-02-09
> **vendax said:**
> I've found one alternative: **doas** which seems lightweight. I am thinking of symlinking sudo to doas and create a working drop-in replacement that way. Will that work?

Doubtful.  sudo is ingrained into most Unix-like OSes.  If you really want to know, spin up a virtual machine and try it.  Be very careful using tools that claim anything security related without 5+ yrs of world-wide use and trust built first.

In my younger years, I created a program to replace sudo for a few very specific needs.  It wasn't long and within a few hours, people in the company had already found new back doors that I'd enabled because I made lots of assumptions, like that the PATH could be trusted.  It cannot. I ended up vastly reducing my program to support less than 10 exact needs.  Once that was handled, no more bugs were found, though I suspect after I left, someone decided that using sudo for the specific need would be safer than leaving unsupported code with root privilege around.

Ubuntu used something called 'polkit' for a few years to launch GUI programs with elevated permissions.  Seems there were always unexpected issues, mostly security related, with that tool.  Do you think the doas team is better than Canonical?

There is much to be said about simpler code.  I'd want to see what some trusted, big-name, security people say about doas.  Since I know nothing about it, haven't used it and don't plan to use it, I won't go any farther.

You can certainly remove many of the Canonical default settings from sudo/sudoers, if you like.  Just be certain you have a Try Ubuntu ISO ready so you can get back in and fix the sudoers when you screw something up.  One day just a few years ago, I was screwing with the sudoers on one of  my systems - actually, adding an automatically included file to /etc/sudoers.d/ with the intent to place that file across all my systems with a devops tool, ansible.  Over and over and over and over, I kept getting locked out from sudo.  I tried all sorts of fixes. None worked.  Then it beat me over the head that I'd used the wrong format for my little config change and it was breaking the sudoers parser completely.  There's a README in that directory which explains the use.

I'm loath to say much more, since the sudoers manpage is really quite excellent and figuring out how to make it work for a single, named, user, seems intuitively obvious to me for anyone with the skills to be considering what you are considering.

---

### Post by SeijiSensei on 2023-02-10
```
sudo iptables -I OUTPUT -i [name of interface] -j DROP
```

Replace [name of interface] with its symbolic name like eno1 or something like wlx18d6c708f58c. This tells the kernel to drop all packets sent out the interface.

If you have a local network, let's say 192.168.1.0/24, you might want to permit traffic to other networked machines but not outside:
```

sudo iptables -I OUTPUT -d 192.168.1.0/24 -j ACCEPT
sudo iptables -A OUTPUT -d 0/0 -j DENY

```

Having a well-populated /etc/hosts file can solve a lot of these issues as well.

---

### Post by vendax on 2023-02-11
It appears doas **CAN** be used as drop-in replacement for sudo and it works instantly with the following commands executed as root:

```
apt install doas
echo "permit: adm" > /etc/doas.conf
rm /usr/bin/sudo
ln -s /usr/bin/doas /usr/bin/sudo
```

Since doas does not connect to the network, it does not have the one-minute stall problem that sudo has whenever it faces an untranslatable hostname. In my opinion, sudo shouldn't engage in any network access. For a security product to engage in networking? Not my cup of tea. But, apparently doas is what i wanted: a simple sudo command to run commands as root from my ordinary user, without contacting the internet, doing network things or doing anything that it shouldn't be doing.

Note: the following output is where 'sudo' is actually a symbolic link to 'doas' as described in the commands above.
```
$ whoami
ubuntu
$ sudo whoami
doas (ubuntu@ubuntu-22.04) password:
root
$ sudo hostname
ubuntu-22.04
$ sudo ping $(hostname)
ping: ubuntu-22.04: Name or service not known
```

MISSION ACCOMPLISHED!!!! Thanks all :)

---

### Post by TheFu on 2023-02-11
If those are the only commands you need, great.  I fear you'll find they aren't and there are some unexpected ramifications.  When/if that happens, please come back and post the issues experienced.

---

### Post by Morbius1 on 2023-02-11
Back many moons ago the sudo error message you received was caused by a hostname mismatch between /etc/hosts and /etc/hostname as explained here:
[https://askubuntu.com/questions/1343609/sudo-unable-to-resolve-host-hostname-temporary-failure-in-name-resolution](https://askubuntu.com/questions/1343609/sudo-unable-to-resolve-host-hostname-temporary-failure-in-name-resolution)

Have things changed?

---

### Post by TheFu on 2023-02-11
> **Morbius1 said:**
> Back many moons ago the sudo error message you received was caused by a hostname mismatch between /etc/hosts and /etc/hostname as explained here:
[https://askubuntu.com/questions/1343609/sudo-unable-to-resolve-host-hostname-temporary-failure-in-name-resolution](https://askubuntu.com/questions/1343609/sudo-unable-to-resolve-host-hostname-temporary-failure-in-name-resolution)

Have things changed?

Good point.  
```
$ sudo ping hostname
ping: hostname: Name or service not known
```
Not sure what that command was supposed to show.  Probably just a typo, but it could mean that the /etc/hosts file isn't setup correctly.  If you want the system to answer to "hostname" like localhost, then that needs to be in the /etc/hosts file.

Perhaps
```
ping $(hostname)
```
is what the OP meant?  IDK.

Anyways, if this is solved, please use the "Thread Tools" button to mark it solved to help others in the community.

---

### Post by vendax on 2023-02-11
@SeijiSensei: thank you sir for your input! However, a firewall is like a second-hand solution to the original problem. I want to deal with the core, namely an operating system that only engages in network activity upon the users' consent. So if i do sudo apt update then that can access the network. But no ntpd running in the background that does network I/O. I want all networks to be silent if the user did not engage in any activity. More specifically, i want to prevent hardware fingerprinting and other profiling from taking place, so i am privacy oriented. Your solution of a firewall is welcome, but i prefer to deal with the origin first and when wireshark is silent on my desired operating system, i will put a firewall in place as additional hardening - not as first-and-final protection. Anything that touches the firewall should light up and receive my attention. But before that i want to fix things not doing stuff i don't want them to, such as sudo engaging in network I/O even with a simple `sudo ls` command.

@TheFu: your warning is welcome and indeed i will report back if doas causes problems. I do understand your argument that sudo is established as security product. Yet, i am stubborn enough to wish to desire a more lightweight solution that does not necessarily cater to the multi-thousand workstation usecase you described, but acts as lightweight alternative that caters to desktop users with just one user account where the user is also the administrator. By good practice, we do not run applications as root without reason, and only gain root privilege by something like 'su' or 'sudo'. In this regard, i find sudo to be a too much enterprise-oriented solution if the default 'sudo whoami' command would want network access. That doesn't sit right with me. So i am trying different solution, doas seems to work for me thus far. It doesn't mean that your caution falls to deaf ears - i do understand i am on an alternative path here. But i'm not running a bank that protects millions of assets, i run a desktop with private data and a desire to protect myself from fingerprinting and thus wanting to control network access/activity.

@Morbius1: yes you did understand and your link is relevant. But the point is that i do not want to fix the hostname being unresolvable at this time. It is a separate issue i might fix later, but it is only that i noticed sudo requiring network configuration for a simple `sudo whoami` command whereas i think this should be working without any interoperability with networking whatsoever. It feels like i am not in control over my own computer. I am no super expert. My effort is to understand better what data leaves my system to the 'evil internet' by watching wireshark. Without me doing anything, i would like wireshark to be completely silent, except for DHCP activity of course.

@TheFu: My apologies! I indeed meant `ping $(hostname)` and not `ping hostname`. The point of my example was to illustrate that i have an untranslatable hostname (so no proper /etc/hosts) but yet doas (symlinked as 'sudo') would still work. Whereas previously with the real sudo, this would give me a one-minute pause because it was waiting for DNS resolution. Because the packets are silently dropped by a hardware firewall, there is a one minute pause. I will edit my previous message to avoid confusion.

For me this issue is fixed, but i do encourage discussion of my choices if anyone cares. I will also report any issues or problems that i encounter by replacing sudo with doas. Thanks all of you for your time and insights!

---

### Post by vendax on 2023-02-11
If i may go into this further, is doas really a compromise as TheFu somewhat suggested?

It is created by an OpenBSD developer, an operating system known for its focus on security and with a long proven track record. To be taken seriously?

Wikipedia states:

**doas was developed by Ted Unangst for [OpenBSD]("https://en.wikipedia.org/wiki/OpenBSD") as a simpler and safer [sudo]("https://en.wikipedia.org/wiki/Sudo") replacement.[SUP][[4]]("https://en.wikipedia.org/wiki/Doas#cite_note-4")[/SUP][SUP][[5]]("https://en.wikipedia.org/wiki/Doas#cite_note-5")[/SUP] Unangst himself had issues with the default *sudo* config, which was his motivation to develop doas.[SUP][[2]]("https://en.wikipedia.org/wiki/Doas#cite_note-:0-2")[/SUP]**

---

### Post by vendax on 2023-02-11
One potential issue i found:

> **Note:** The persist feature is disabled by default and because it is new and potentially dangerous. In the original *doas*, a kernel API is used to set and clear timeouts. This API is OpenBSD specific and no similar API is available on other operating systems. As a workaround, the persist feature is implemented using timestamp files similar to *sudo*.
Taken from: [https://wiki.archlinux.org/title/Doas](https://wiki.archlinux.org/title/Doas)

PS i love that they talk about symlinking sudo to doas as a *Smooth transition sudo to doas* - just as i intended. :KS

---


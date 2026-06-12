---
title: "Upgrade Lubuntu 11.04 to 12.04"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by apochry on 2012-11-02
Hello, 

I have an old machine running Lubuntu 11.04 (desktop release) that I use as a file/printer/scanner sharing server at home.  I have never been prompted for system upgrades on that machine, although i have the right settings set in the update manager (under the updates tab it is set to notify me for new versions).
I want to upgrade the machine to 12.04 since it is LTS release.

Should I do that, or better not... what do you think? (11.04 is not supported anymore, as far as I know).
If yes, how should I do that? I can't make the machine see the any new available OS upgrades (I was getting updates regularly). I guess it will work with a live USB...

Any suggestion will be highly appreciated!
Thank you!

- Christo

---

### Post by Rex Bouwense on 2012-11-02
I prefer to do a new install over upgrade since the upgrade would involve upgrading from 11.04 to 11.10 and then from 11.10 to 12.04.  Now Lubuntu 12.04 is not an LTS as Ubuntu 12.04 is.  You are correct in that support for 11.04 stopped last month.  A new install will take less time and has (in my opinion) a better chance of being successful than an upgrade but that is your call.  In any event back up anything that you cannot afford to lose.

---

### Post by apochry on 2012-11-02
Thanks for the reply Rex!

I was hoping to save myself some setting up of mounts, shares, scanner and printer with an upgrade.
I now realize that Lubuntu 12.04 is not a LTS... so there is no Lubuntu LTS, is this right?

What are the downsides of running a not supported *ubuntu? I know I won't get security updates and so on, but this is not critical for me since the "server" is in a closed home network behind firewall (correct me if I'm wrong on this).
I don't actually feel that the server needs an upgrade (or a new install), the machine is absolutely stable and does the job it stays for. The only think that bugs me is that 11.04 is not supported anymore.

- Christo

---

### Post by kalehrl on 2012-11-03
> so there is no Lubuntu LTS, is this right?You're right.
There is no Lubuntu LTS.
As I understand it, you will still be able to connect to Ubuntu repositories and update packages and download and install stuff because Lubuntu is based on Ubuntu and they share the same system. You won't receive updates for Lubuntu stuff. I myself am stuck with 12.04 because of Pentium M processor.

---

### Post by apochry on 2012-11-03
What is the problem with 12.10 and the Pentium M processor? My, so called, server has a Celeron M and I guess it will be the same as by your Pentium M.

---

### Post by MG&amp;TL on 2012-11-03
> **apochry said:**
> What is the problem with 12.10 and the Pentium M processor? My, so called, server has a Celeron M and I guess it will be the same as by your Pentium M.

Some processors have problems with PAE (I believe it's a CPU feature in older CPUs) and the new kernel (I.e. won't boot at all). 

Lubuntu team wanted to keep support for it, but we just don't have the manpower to maintain a separate kernel to the rest of *buntu. Give it a try: there is two possible outcomes:

1) Error message on boot, to do with PAE. You've got problems.

2) Boots fine, or with different error. You haven't got problems to do with PAE.

---

### Post by kalehrl on 2012-11-03
Or, you can check if it supports PAE beforehand with this simple command:
```
cat /proc/cpuinfo | grep pae
```

---

### Post by apochry on 2012-11-04
```
eli@eli-PC:~$ cat /proc/cpuinfo | grep pae
flags        : fpu vme de pse tsc msr **[COLOR=Red]pae[/COLOR]** mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts

```

I guess this says it does, right?

---

### Post by dino99 on 2012-11-04
> **apochry said:**
> ```
eli@eli-PC:~$ cat /proc/cpuinfo | grep pae
flags        : fpu vme de pse tsc msr **[COLOR=Red]pae[/COLOR]** mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts

```

I guess this says it does, right?

exact, you are lucky, no kernel problem on that pc with 12.10 :P

note: as the old kernel is no more built, now into archive the kernel is named "generic" , but is in fact a pae one.

---

### Post by apochry on 2012-11-04
Nevertheless, I seems that an upgrade will be difficult, going  trough two releases in third, which isn't LTS either. And there is very  good possibility something to go wrong. 
On the other hand a fresh  install will need all the configurations done to the current setup  (setting up printer, scanner, mounts, shares, vnc, etc...). Not that is a  lot of work, but I'm bored to do it again. It's fun only the first  time. :-)

My main problem is that Lubuntu doesn't have LTS  releases. Hence, it seems that it isn't much suitable for a small home  server, since even the latest install will  go unsupported in an year  and a half or so... Can you recommend a lightweight distro which will  suit better for this purpose? I will need a GUI since I'm not that deep  in LINUX and my flatmate - not a Linux guy - has to be able to do some simple tasks on the  machine (e.g. scanning, browse shares from there). It seems to me that "Ubuntu Server  12.04.1 LTS" with LXDE installed will be best...

Thank you!
 - Christo

---

### Post by MG&amp;TL on 2012-11-04
> **apochry said:**
> 
My main problem is that Lubuntu doesn't have LTS  releases.

Well...it sort of does.

Okay:

-Things that Lubuntu team does (basically interface stuff, some tweaks to the openbox configuration) will **not** be updated.

-Everything else will receive updates as per usual with *buntu.

Hope that helps a bit.

---

### Post by apochry on 2012-11-04
> **MG&TL said:**
> Hope that helps a bit.

It does! I understand *ubuntu distros better now . :-)

And I have made my mind too... I will probably go for Ubuntu Server LTS and install a lightweight GUI next time, when I feel like tinkering on the old machine.

Thank you all for the helpful replies!

Regards,
 - Christo

#Marking thread as solved.

---


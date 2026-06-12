---
title: "Booting problem"
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by satimis on 2018-05-01
Hi all,

Ubuntu 18.04 desktop

On booting following warning popup```

fail to connect lvmetad falling back to device scanning
....

```

It waits for long time but finally it boots

What is the warning?

I couldn't find this warning on /var/log/boot.log ?

Regards
satimis

---

### Post by rsteinmetz70112 on 2018-05-01
It means the lvm daemon is not started yet. This happens when the root system or especially /boot is in a logical volume and needed to continue startup. It doesn't mean anything much. You might be able to eliminate it by forcing lvm2 to start sooner. 

When you say it waits a long time who long are you seeing. I have several systems set up this way and there is a wait but it isn't that long

---

### Post by satimis on 2018-05-01
> **rsteinmetz70112 said:**
> It means the lvm daemon is not started yet. This happens when the root system or especially /boot is in a logical volume and needed to continue startup. It doesn't mean anything much. You might be able to eliminate it by forcing lvm2 to start sooner. 

When you say it waits a long time who long are you seeing. I have several systems set up this way and there is a wait but it isn't that long
Hi,

Thanks for your advice.

Just checked it.  The waiting time is about 45 sec after the warning.

Ubuntu 16.04 doesn't has this symptom.  It only waits about 4~5 sec after the warning.

Regards
satimis

---

### Post by rsteinmetz70112 on 2018-05-02
> **satimis said:**
> Hi,

Thanks for your advice.

Just checked it.  The waiting time is about 45 sec after the warning.

Ubuntu 16.04 doesn't has this symptom.  It only waits about 4~5 sec after the warning.

Regards
satimis

I haven't upgraded to 18.04 yet so I'm still running 16.04 LTS. Are your root and or boot on a logical volume? If so I'd consider filing a bug. 45 seconds is a long time. especially since 16.04 only takes a few seconds.

---

### Post by satimis on 2018-05-02
> **rsteinmetz70112 said:**
> I haven't upgraded to 18.04 yet so I'm still running 16.04 LTS. Are your root and or boot on a logical volume? If so I'd consider filing a bug. 45 seconds is a long time. especially since 16.04 only takes a few seconds.
Thanks

It is raw installation on ubuntu-18.04-desktop-amd64.iso, not upgrade.  It seems the newly published Ubuntu-18.04 desktop is not very stable.  There are some other issues and you'll find some links on Internet complaining this version.

I'll cease testing Ubuntu 18.04 until it become stable.

Regard
satims

---

### Post by rsteinmetz70112 on 2018-05-03
> **satimis said:**
> Thanks

It is raw installation on ubuntu-18.04-desktop-amd64.iso, not upgrade.  It seems the newly published Ubuntu-18.04 desktop is not very stable.  There are some other issues and you'll find some links on Internet complaining this version.

I'll cease testing Ubuntu 18.04 until it become stable.

Regard
satims

I run the LTS version on several machines. I never upgrade them until the .1 version, that's also the first point at which a automatic upgrade is offered by Synaptic.

---

### Post by dino99 on 2018-05-03
To get details, run 'journalctl -b' into a terminal ! bright line (warning), red line (error)  :P

---

### Post by satimis on 2018-05-04
> **dino99 said:**
> To get details, run 'journalctl -b' into a terminal ! bright line (warning), red line (error)  :P
Following lines are in red color```

May 04 12:30:14 ub1804pc1a00 kernel: Spectre V2 : Spectre mitigation: LFENCE not serializing, switching to generic retp
May 04 12:30:21 ub1804pc1a00 spice-vdagent[1242]: Cannot access vdagent virtio c

May 04 12:30:44 ub1804pc1a00 pulseaudio[1613]: [pulseaudio] bluez5-util.c: GetMa&#9474;··

```

satimis

---


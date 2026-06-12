---
title: "Intel Audio Driver No Longer Loads"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by milliman on 2008-10-18
I have an Intel 828001DB AC '97 audio controller that has worked perfectly with PulseAudio and Hardy.  It worked in Intrepid until earlier this week after a distro update.  It seems that the audio driver module is no longer loading in the kernel because of errors.

This is my audio controller output of lspci:```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
```

When I try to manually load the module I receive the following error:```
mmilliman@Coronado:~$ sudo modprobe snd_hda_intel
[sudo] password for mmilliman: 
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I have noticed that other people are experiencing this problem, but the only replies are related to removing or reinstalling PulseAudio.  PulseAudio is not the problem when the modules don't load in the kernel. My audio works perfectly under my old 2.6.27-6 kernel.

I am not very familiar with the driver structure in Linux so I don't know how to fix the problem.  Is there possibly another module in another directory that I can use in place of this one?  Do I need to rebuild the module under the new kernel headers?  I keep hoping for an update that will fix the problem, but haven't received one.

Any ideas or assistance is greatly appreciated.  This could help many people like me.

---

### Post by psyke83 on 2008-10-18
> **milliman said:**
> I have an Intel 828001DB AC '97 audio controller that has worked perfectly with PulseAudio and Hardy.  It worked in Intrepid until earlier this week after a distro update.  It seems that the audio driver module is no longer loading in the kernel because of errors.

This is my audio controller output of lspci:```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
```

When I try to manually load the module I receive the following error:```
mmilliman@Coronado:~$ sudo modprobe snd_hda_intel
[sudo] password for mmilliman: 
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I have noticed that other people are experiencing this problem, but the only replies are related to removing or reinstalling PulseAudio.  PulseAudio is not the problem when the modules don't load in the kernel. My audio works perfectly under my old 2.6.27-6 kernel.

I am not very familiar with the driver structure in Linux so I don't know how to fix the problem.  Is there possibly another module in another directory that I can use in place of this one?  Do I need to rebuild the module under the new kernel headers?  I keep hoping for an update that will fix the problem, but haven't received one.

Any ideas or assistance is greatly appreciated.  This could help many people like me.

Your problem has nothing to do with PulseAudio. Did you rebuild the ALSA kernel modules manually?

---

### Post by milliman on 2008-10-18
That's what I said. It is NOT a PulseAudio problem.  PulseAudio works perfectly under my older kernel.  

I am not sure what package has my drivers and how to rebuild them.  I suppose if I know the package name I can use apt or Synaptic Package manager to reinstall them.

Please let me know what packages these drivers are in.

Thanks.

---


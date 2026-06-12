---
title: "Random Kernel Panics"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by syko21 on 2008-09-29
I am running latest 32 bit intrepid as of this posting. My hardware is
C2D T5600 1.83GHz
2gb RAM
Nvidia 7400 Go (issue does not change whether I use nv driver or 177.70 self compiled)
Intel 4965agn

In the last 24 hours I've had at least 4 kernel panics. I understand that this is a developmental release and I'm not complaining. But how do I write a bug report when the log files from the last few seconds before the panic never get written and there is no consistency to the panics? (At least no visual consistency, it doesn't happen when I'm running any particular application) Some times at reboot it kernel panics when gdm starts up and the mouse icon is using the busy rotating icon.

2 Questions then, how can I track the kernel panics to submit a bug report?, and is anyone else having this issue?

---

### Post by Hairy_Palms on 2008-09-29
well none of the hardy kernels even let me boot, kernel panic as soon as ive picked them from grub, and likewise i have no idea how to get the logs

---

### Post by syko21 on 2008-09-29
just wanted to add that I installed the kerneloops package but I don't know how to use it properly

---

### Post by nanog on 2008-09-29
If you can get a stable system in another kernel (e.g. 2.6.24) then just go to /var/log and upload copies of dmesg and kern.log along with a description of exactly what is needed to induce the panic. If you cannot get a stable kernel boot with a live cd and mount your hard drive to access log files. If there no errors  in the log files then be sure to take a photo of the screen during kernel panic and attach to your bug report. If the panic occurs during boot you may want to remove the quiet flag from your boot options.

---

### Post by syko21 on 2008-09-29
I just had 6 kernel panics in the last 2 hours. I have to downgrade to hardy, I can fix bugs when I know where the problem program is but I have no clue what to do with the kernel... Thanks anyway and hope the release is stable at launch

---

### Post by Hairy_Palms on 2008-09-30
you could always do what im doing syko, run intrepid with hardys kernel, that way you can test and use everything else.

---

### Post by syko21 on 2008-10-01
Ok so I think I've determined a common link. Every time I kernel panic I am using a router with wireless N capability. I attempted to make my machine panic at my university (Pure 802.11b network only) and no matter what everything was fine. Is there a way to disable N speeds on a 4965 card or should using the old iwl4965 drivers work to limit it to ABG only?

---

### Post by psyke83 on 2008-10-01
> **syko21 said:**
> I am running latest 32 bit intrepid as of this posting. My hardware is
C2D T5600 1.83GHz
2gb RAM
Nvidia 7400 Go (issue does not change whether I use nv driver or 177.70 self compiled)
Intel 4965agn

In the last 24 hours I've had at least 4 kernel panics. I understand that this is a developmental release and I'm not complaining. But how do I write a bug report when the log files from the last few seconds before the panic never get written and there is no consistency to the panics? (At least no visual consistency, it doesn't happen when I'm running any particular application) Some times at reboot it kernel panics when gdm starts up and the mouse icon is using the busy rotating icon.

2 Questions then, how can I track the kernel panics to submit a bug report?, and is anyone else having this issue?

I recommend that you use the ethernet connection and install SSH. When the kernel panics, try to gain access to a shell prompt via another machine. When you gain access, check the tail section the kernel logs.

Also try the [special keystroke]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_Mnemonic_Device") to see if you can restore access to your machine, or at least coax the machine to safely reboot the machine to allow logs to be saved.

---

### Post by syko21 on 2008-10-02
I've tried the REISUB magic keys several times but its a completely dead machine. HOWEVER!, I have found something that works and I think it should be added to the official repository, the Oct-1-2008 compat-wireless iwlagn module fixes the kernel panic issue. I've left my machine on for an extended period of time in the same conditions that used to kernel panic before and so far all is good. I understand we are nearing the end of the road and only major showstoppers should be included for release but I feel this warrants such consideration.

---

### Post by RAOF on 2008-10-02
> **syko21 said:**
> ...I have found something that works and I think it should be added to the official repository, the Oct-1-2008 compat-wireless iwlagn module fixes the kernel panic issue. I've left my machine on for an extended period of time in the same conditions that used to kernel panic before and so far all is good. I understand we are nearing the end of the road and only major showstoppers should be included for release but I feel this warrants such consideration.

You should definitely attach this information to a bug filed against the "linux" package on [Launchpad](launchpad.net).  No one connected with Ubuntu's kernel will find this information here!

---

### Post by syko21 on 2008-10-02
I just did. If anyone would like to post new or relevant information please do so here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)

I am also conducting a poll in another post to see if there are others who are affected by this issue. If you have an intel 4965 card or use the iwlagn driver for your card please vote on this thread [http://ubuntuforums.org/showthread.php?t=935731](http://ubuntuforums.org/showthread.php?t=935731)

---


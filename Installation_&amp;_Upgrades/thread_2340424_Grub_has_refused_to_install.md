---
title: "Grub has refused to install"
date: 2016-10-18
forum: Installation &amp; Upgrades
---

### Post by nicksamurai on 2016-10-18
Hi, i am a firs time installer of Ubuntu. And so far no one else seems to wnt to help me please help me find out my issue. The URL i got from boot info is 
[http://paste2.org/V7MN1pbx](http://paste2.org/V7MN1pbx)

---

### Post by nicksamurai on 2016-10-18
Link again, i did an error [http://paste2.org/V7MN1pbX](http://paste2.org/V7MN1pbX)

---

### Post by QIII on 2016-10-18
Hello!

Would you clearly state the behavior you would like help with?

Thanks!

---

### Post by nicksamurai on 2016-10-18
grub isnt installing and i cannot boot to Ubuntu other than if i run the live disk

---

### Post by QIII on 2016-10-18
What do you mean by "isn't installing"?  The more detailed your description the easier it will be to help.

Vague descriptions offer little to aim at.  

Please provide details on what you see.  The more detail you give, the easier it will be to look at specific areas of the boot report.

---

### Post by nicksamurai on 2016-10-18
When i tried to repair GRUB this error came 'grub install error cannot find EFI.' any method i try always gets back to this.

---

### Post by yancek on 2016-10-18
> When i tried to repair GRUB this error came 'grub install error cannot find EFI.' any method i try always gets back to this. 		

That's because you don't have an EFI install and therefore there is no EFI partition.  You have a standard MBR boot and the Master Boot Record contains windows code which won't boot Ubuntu or any other Linux without going through a convoluted process.  You didn't use the correct option for the Grub install.  Boot the flash drive and select the Try Ubuntu option and when you get to the Desktop, open a terminal and type:  sudo grub-install /dev/sda

That will put Grub code in the MBR and you should be able to boot Ubuntu.  For some reason, you do not have a windows entry in the grub.cfg file so when you boot the Ubuntu on the hard drive, again open a terminal and run:  sudo update-grub  Watch the output for a windows entry.

---

### Post by oldfred on 2016-10-18
How you boot install media is then how it installs.
And with Windows in BIOS/MBR configuration, you need to have Ubuntu/grub in BIOS boot mode.

So you can tell which mode you boot in, but UEFI boot menu should show both if Secure boot is off.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by nicksamurai on 2016-10-21
thank you, let me try. I appreciate the solution.

---

### Post by nicksamurai on 2016-10-24
i found a solution thank you very much for your help. I apparently i was installing grub in the wrong place. Noob behaviours. Just glad i did not mess anything up. Than you so much.

---


---
title: "Found out it's a dual HD drive setup.."
date: 2015-01-02
forum: Installation &amp; Upgrades
---

### Post by garpt01 on 2015-01-02
OK,
  I got my questions answered regarding taking the step for a new install in another thread.  This is a new issue (I didn't remember I have dual HD installation.)

This is how the machine is configured:

Ubuntu 11.04 currently on dev/sda1
windows loader on dev/sdb1
windows 7 install on dev/sdb2

  
the installation of 14.04 is asking me where I want to put the bootloader. That's where I'm stuck. 

P.S. There is another Windows bootloader on dev/sdc1. Not sure which one is actually working, but the sdc1 file size is substantially larger. 

Currently, When I boot the machine, it goes into the Windows loader, I choose Ubuntu (or it defaults to Windows), then it takes me to the Ubuntu grub loader where there are several older kernels listed. It has been working great like this for almost 4 years, and I like it even though I know it sounds messed up! But Ideally, I would like to simply install the new Ubuntu from my CD into its current location without "breaking" the loader(s). Possible?

Thanks! I won't proceed with anything yet.....

---

### Post by MAFoElffen on 2015-01-02
/dev/sda.

But why are you installing 11.04 instead of 12.04 LTS or 14.04LTS/ You know that 11.04 is unsupported because it has been End of Life for many years now right?

---

### Post by garpt01 on 2015-01-02
I know that.
 I *currently* have 11.04 and want to replace it. I want to install a New, Fresh version- 14.04.1, and I don't know where to mount the bootloader with my 2 HD system described above. Please re-read my post. I'm going to hope I get some help before retiring for the evening. 

Thanks All

P.S.: Thanks
**[SIZE=4][COLOR=#ff0000]MA[/COLOR][[COLOR=#ff0000]FoElffen[/COLOR]]("http://ubuntuforums.org/member.php?u=1044547")[/SIZE]**[SIZE=3] I missed the upper corner where you posted /dev/sda. I'm going to give it a try! At least I know (believe) I can't mess up my Windows since it's on a separate HD![/SIZE]

---


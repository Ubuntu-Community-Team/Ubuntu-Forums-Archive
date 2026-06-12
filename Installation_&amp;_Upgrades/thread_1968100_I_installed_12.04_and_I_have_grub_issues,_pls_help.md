---
title: "I installed 12.04 and I have grub issues, pls help me."
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by ricardo072 on 2012-04-28
Hi All,

I have dual-boot on my machine, I had Windows and Open Suse,.. and I was using grub 1.5 (I am not sure about the version)... but I just installed Ubuntu 12.04 on the same partition I was using Suse...

After the installation,... grub stop working... right now I am using the Ubuntu 10.10 CD-live.. 

do you know how can I fix grub ?

Thanks,
Best regards.

---

### Post by darkod on 2012-04-28
If you installed 12.04 why are you using 10.10 to boot into live mode?

You will need to reinstall grub2 from the cd with the same version as the one you have installed.

To make sure what you have installed and where, you better run the boot info script from the link in my signature. Post the results as explained there.

---

### Post by oldfred on 2012-04-28
It sounds like you Open Suse was using grub legacy. Ubuntu is using grub2 which is a lot different. But either way it should be installed to the MBR or sda so it boots.

One of the easiest gui ways and if it does not work post the link from the Bootinfo report:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

Info on grub2:
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by zdeuyo on 2012-04-28
> **ricardo072 said:**
> Hi All,

I have dual-boot on my machine, I had Windows and Open Suse,.. and I was using grub 1.5 (I am not sure about the version)... but I just installed Ubuntu 12.04 on the same partition I was using Suse...

After the installation,... grub stop working... right now I am using the Ubuntu 10.10 CD-live.. 

do you know how can I fix grub ?

Thanks,
Best regards.

Hello,

I had a similar problem and Boot-Repair fixed it about 1 hour ago on this computer I am writing this from. Here is the link

Link: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Follow the instructions exactly on that page.

Let me know if it works.

---

### Post by ricardo072 on 2012-04-28
Hello,

Thank you All for your help... but I fixed the issue re-installing Ubuntu 10.04 on the same disk I had ubuntu 12.04,... now I have grub working fine..

but now my problem is,... how can I update Ubuntu 10.04 to 12.04 ??

The Update Manager displays that (of course) this release is no longer supported... what can I do ?

---

### Post by oldfred on 2012-04-28
If it is 10.04 as LTS it should let you update directly to 12.04. But anything else is each 6 month version or else a clean install.

---

### Post by darkod on 2012-04-29
I don't agree that a solution to a problem is going back to a version 2yrs old. But the choice is yours.

If you only provided the results with the details of your system, maybe the fix was easy.

You will not be able to upgrade directly to 12.04 until 12.04.1 gets released in July.

First of all, in Software Sources - Updates select the option to prompt you for upgrade only for Long Term releases, otherwise it will try to upgrade the 10.04 to 10.10 not to 12.04.

It's not true that 10.04 is not supported any more, it still has 1yr of support. Are you sure that is the version you installed?

You can also force it to upgrade to 12.04 before July by running in terminal:
sudo update-manager -d

But first make sure you have the setting for Long Term releases as I said above to make sure it will upgrade you to 12.04.

---

### Post by ricardo072 on 2012-04-30
Ok, going to double-check what is the right version... I think it is Ubuntu 10.10 (I'm guessing right now)...


======================================
Adding some info...
- I just installed Ubuntu 12.04
- I had some issues to boot, which I have fixed following this post:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Thank you all for your help.
Best regards.

---


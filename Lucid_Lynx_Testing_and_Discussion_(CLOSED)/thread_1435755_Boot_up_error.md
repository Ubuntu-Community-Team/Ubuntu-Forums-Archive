---
title: "Boot up error"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Fred the Penguin on 2010-03-21
When I boot up Lucid alpha 3, I get an error message. I checked syslogs  in log file viewer and I think I found the right error it is: Mar 21 21:14:26 jonathan-laptop kernel: [   17.912253] nForce2_smbus 0000:00:03.2: Error probing SMB2.
           I would appreciate someone telling me how to fix this.  I think it slows down my boot time.

---

### Post by collinp on 2010-03-21
I believe you may be experiencing this bug: [Bug #440470 in linux (Ubuntu): "[ubuntu-boot-experience] nForce2_smbus conflicts with ACPI region SM00"]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440470")

A possible workaround, listed in the comments of that bug, would be to add "acpi_enforce_resources=lax**" **as a kernel boot option.

Read this post on how to add kernel boot options to Grub2: [http://ubuntuforums.org/showpost.php?p=8570970&postcount=2](http://ubuntuforums.org/showpost.php?p=8570970&postcount=2)

---

### Post by Fred the Penguin on 2010-03-22
Thank you. That is the right bug, but where do I add the line to grub file? I added it  after **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
     Here is the grub file after I added "acpi_enforce_resources=lax"      :# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" ***"acpi_enforce_resources=lax"***
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


Did I add the line in the right place because I get this when I try to update grub:
/etc/default/grub: 9: acpi_enforce_resources=lax: not found
I am afraid to reboot in case I messed something up.

---

### Post by psusi on 2010-03-22
You don't add a second set of quotes, you just add that to the existing quote.

---

### Post by Fred the Penguin on 2010-03-22
Thank you psusi! My laptop doesn't have that error anymore and It shuts down in under 5 seconds. It used to take nearly 20.

---


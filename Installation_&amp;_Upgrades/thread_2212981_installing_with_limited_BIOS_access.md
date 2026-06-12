---
title: "installing with limited BIOS access"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by rene7 on 2014-03-24
ok, so, I'm gonna throw this into the great and powerful Ubuntu community and hope for the best..

I am trying to install Ubuntu on my gf's laptop.
some issues:
[LIST=1]
[*]BIOS setup is blocked with a password which I don't have.
[*]BIOS setup has blocked USB or CDROM options from the boot sequence
[*]removing the CMOS battery from the MoBo has not been able to reset the BIOS setup password (it did reset time and date however)
[/LIST]

Sofar I've been able to remove the onboard HDD, attach it to my own PC, install it asif it were a USB stick and set the Ubuntu install disk on there.
This way the laptop will boot into the installer menu.
Problem is then that the install cannot install onto the same HDD because part of the installation is modifying the MBR, which is impossible as long as the disk is in use.
However, I have been able to install Ubuntu onto an external harddrive (USB connected) and when I tell the installer to set the boot record to the internal HDD, that will somewhat work.
I had hoped that, from the installed OS on the external harddrive, I would be able to access a USB with the Ubuntu install disk and install Ubuntu on the then unused internal HDD. Sadly that will not work.

Now I ask onto you, Ubuntu Community, help!

Thank you  :)

---

### Post by Elfy on 2014-03-24
Why can't you get the password - does the gf not know it or know where to get it from?

---

### Post by ajgreeny on 2014-03-24
It might be possible to put the hard-drive from your gf's machine into another machine (as similar as possible to hers) and install ubuntu that way, making sure you don't choose to update and add restricted packages at the same time.  Replace the drive back into your gf's machine and see if it will boot into ubuntu; with luck it will do so, and you can then update and install any proprietary drivers etc etc.

Without the ability to get into the BIOS even that may not be possible, and I think you must try really hard to find that password or you could continue to have big problems when you want to upgrade the OS to the next version.

---

### Post by rene7 on 2014-03-24
@ Elfy: no, no clue what it is or where to get it from. I was advised to try n reset the BIOS settings by removing the battery, but that did not remove the password as I had hoped.

@ AJGreeny: I had thought of that, haven't been able to find someone with a similar laptop yet tho. How flexible would the Ubuntu install be in such a case tho? would it not record MAC addresses or hardware ID's of computer parts or something?

---

### Post by bapoumba on 2014-03-24
> **rene7 said:**
> @ Elfy: no, no clue what it is or where to get it from. I was advised to try n reset the BIOS settings by removing the battery, but that did not remove the password as I had hoped.


Where does the machine come from ?

---

### Post by Mark Phelps on 2014-03-24
> I am trying to install Ubuntu on my gf's laptop.
some issues:

    BIOS setup is blocked with a password which I don't have.
    BIOS setup has blocked USB or CDROM options from the boot sequence
    removing the CMOS battery from the MoBo has not been able to reset the BIOS setup password (it did reset time and date however)

This sounds EXACTLY like the situation that I encountered when I was working with a laptop my company had issued me.  They had it completely locked down so no changes could be made to it, including password-protecting the BIOS and fully-encrypting the hard drive.

Sorry,  but if this is the case with your GF's laptop, and you've tried replacing the drive, there is really nothing you can do.

---

### Post by rene7 on 2014-03-24
@ Bapoumba: I believe this laptop was once issued to her from her school

@ Mark Phelps: replacing the drive (small SATA) seems redundant, it can be formatted and reused, I had no difficulties when I attached it to my own PC.

---

### Post by bapoumba on 2014-03-24
> **rene7 said:**
> @ Bapoumba: I believe this laptop was once issued to her from her school


So who is the owner now ? You may want to go back to the school and work that out. If they give her ownership of the machine, they should give her the passwords with it. If not, the machine belongs to them and you should not circumvent their setup.

---

### Post by Elfy on 2014-03-24
When you've dealt with the provenance of the machine and have dealt with the locked BIOS you are welcome to come back for help with those issues, but for the moment I'm closing this thread.

---


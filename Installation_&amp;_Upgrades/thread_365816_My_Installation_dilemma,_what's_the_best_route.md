---
title: "My Installation dilemma, what's the best route?"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by MgNate on 2007-02-20
I recently bought my hp computer and unfortunately they don't give you a windows cd with it anymore, so all i have are these stupid restore cd's. 

So if i were to put linux on the disk drive and then  put the restore disk in it will just delete linux. 

I have a 120gig HD and a 64 bit AMD processor and i want to take advantage of my 64 bit processor. 

I'm having issues running the live cd too. 

*Any help would be greatly appreciated. Thanks.*

---

### Post by idheath on 2007-02-20
Hi,

So what's on your PC at the moment?

Assuming you're starting from an empty system you could to a restore with you Windows restore CD which will take all of the disk space for Windows (I assume).

Then use something like Partition Magic to shrink the Windows partition so that you have space to install Ubuntu too.

Alternatively have you considered running Windows inside VMware?  If so you need to install just Ubuntu then install VMware server (it's free by-the-way).  Then you can run Windows as a virtual machine.

The only possible problem you might have with this 2nd option is if your Windows restore disk is too-clever (i.e. it might check the target machine when you restore it and this probably won't be detected properly from within a virtual machine so the restore might fail).

The 3rd option is to start with just a Windows restore then image the machine using Ghost so that you've got an .ISO file.  Next use an available utility to convert this image to a virtual machine for VMware, then copy this file off the machine.  Next wipe the machine and install Ubuntu and then install VMware and use the virtual machine you saved.

Cheers Ian

---

### Post by MgNate on 2007-02-20
> **idheath said:**
> Hi,

So what's on your PC at the moment?

Assuming you're starting from an empty system you could to a restore with you Windows restore CD which will take all of the disk space for Windows (I assume).

Then use something like Partition Magic to shrink the Windows partition so that you have space to install Ubuntu too.

Alternatively have you considered running Windows inside VMware?  If so you need to install just Ubuntu then install VMware server (it's free by-the-way).  Then you can run Windows as a virtual machine.

The only possible problem you might have with this 2nd option is if your Windows restore disk is too-clever (i.e. it might check the target machine when you restore it and this probably won't be detected properly from within a virtual machine so the restore might fail).

The 3rd option is to start with just a Windows restore then image the machine using Ghost so that you've got an .ISO file.  Next use an available utility to convert this image to a virtual machine for VMware, then copy this file off the machine.  Next wipe the machine and install Ubuntu and then install VMware and use the virtual machine you saved.

Cheers Ian

I used the restore disks to put windows on my system, so at the moment i have windows xp media center edition.


I was going to shrink the partition but i put my ubuntu live dvd in and it didn't work. I actually downloaded again and burnt it again and still no luck. So i tried for the third time and it still won't run the live linux dvd. If i shrink it with partition magic will it help? I'm afraid that after i do that it still own't run. I just want linux and windows on my system, i guess this is the world of linux... That's okay though I'm determined...

Thanks for the help so far and thanks for any other help in advance,

     Nate

---

### Post by bandie on 2007-02-20
Sometimes the Live CD just does not work, ive had install issue on two laptops one old one very new. The best way round the problem (for me anyway) is to use the alternate CD this will install Ubuntu on your chosen partition. The alt CD is downloaded from the Ubuntu site.

---

### Post by MgNate on 2007-02-20
Well I guess I'll try the alternate installation option then. 

Will i be able to partition my HD with the alternate cd? 

Or should i use partitionmagic or something first and then try to install linux off the alternate cd?

What bothers me is that before i restored windows the live cd worked fine, I didn't change any hardware. I just restored to the way it was when i got it, which was the beginning of January. I really don't want to download linux again too. I've already done it 5 times altogether.

But i will get Linux! I'll try whatever method will be best when i get home today in 4 hours, I'm at work.

---

### Post by MgNate on 2007-02-21
For some reason when i tried the alternate cd, it didn't work. For i figured just for the heck of it i'll try the first cd i made and it worked! I'm using Linux right now and i couldn't br happier with it!

---


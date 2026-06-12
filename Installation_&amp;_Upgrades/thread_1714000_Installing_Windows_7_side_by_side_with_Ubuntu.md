---
title: "Installing Windows 7 side by side with Ubuntu"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by nvdkgm on 2011-03-24
I would like to install Windows 7 side by side with Ubuntu. The entire disk was wiped clean and Ubuntu was installed on it. After this I used a liveUSB with Gparted to create free space by resizing because of the weird requirement of Windows installer. Now I have a reasonable sized free space of unformatted but the Windows 7 installer keeps telling me not enough free space so I was wondering what would be causing the error. I asked here because any change to make this work would be on Ubuntu.

Thanks in advance.

---

### Post by wilee-nilee on 2011-03-24
> **nvdkgm said:**
> I would like to install Windows 7 side by side with Ubuntu. The entire disk was wiped clean and Ubuntu was installed on it. After this I used a liveUSB with Gparted to create free space by resizing. Now I have a reasonable sized free space but the Windows 7 installer keeps telling me not enough free space so I was wondering what would be causing the error.

Thanks in advance.

Take a screen shot of gparted and post it, use the paper clip in the reply panel to attach the img.

---

### Post by nvdkgm on 2011-03-24
Attached is how my hard drive is set up as seen in GParted.

---

### Post by wilee-nilee on 2011-03-24
Your lucky, if it had installed it would have probably made the Ubuntu unallocated. Windows 7 without a pre formatted ntfs partition installs 2, the first a 100mib for boot the second for the OS.

To get around this make that unallocated open space a ntfs then right click it-manage flags and click boot with gparted. Boot the windows install and install to that partition, everything in one partition. 

If you want more then one partition in there just make the first one sized to whatever works install then make the second.

---

### Post by nvdkgm on 2011-03-24
Still getting the same error after labeling as ntfs and boot. The question I have is what does flagging it as boot do because I am running the Windows installer from USB?

What next?

---

### Post by wilee-nilee on 2011-03-24
> **nvdkgm said:**
> Still getting the same error after labeling as ntfs and boot. The question I have is what does flagging it as boot do because I am running the Windows installer from USB?

What next?

Having the ntfs flagged as boot makes it active for install, post another shot of gparted. This should be working like 100% of the time.

Are you sure your not pointing the install at the unallocated at the beginning of the hd, in the install you should be choosing that formatted partition.

---

### Post by nvdkgm on 2011-03-25
I am not sure how to point the Windows Installer to that volume because it doesn't give me that option before the error. I am using a .iso and launching the setup within Ubuntu. I click Install now and it straight away gives me a free space error. I have attached the image of GParted after formatting to ntfs and adding boot flag. Not sure if it needs the "/" as a mount point on where to boot or if it is fine as a primary partition rather than a logical drive, since primary was the only option.

---

### Post by AndyCinDallas on 2011-03-25
You could always wipe the drive, install Win 7 first and then install Ubuntu afterwards eg with Wubi - it's an option, at least. I'm concerned that installing Win7 after Ubuntu will cause Win to overwrite the boot-instructions.

---

### Post by oldfred on 2011-03-25
I do not think you can just launch the windows ISO from Ubuntu. You have to create a bootable CD or USB with the windows ISO file and directly boot that.

---


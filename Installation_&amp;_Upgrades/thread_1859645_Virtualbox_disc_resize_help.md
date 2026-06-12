---
title: "Virtualbox disc resize help"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Kaizoku001 on 2011-10-14
Virtualbox disc resize help

I installed a win 7 (64) in virtualbox 4.1.2 with a HD of 100 gig.
I would like to boost it to 200 and would like to know how to do this.
*I tried to use :*
VBoxManage modifyhd Win 7.vdi --resize 200000

But it won't accept the '7.vdi'
I'm beginning to think I might need to upgrade to 4.1.4; which would still leave me with the question

**What command do I use to resize my HD**

Help appreciated

---

### Post by teachop on 2011-10-14
> **Kaizoku001 said:**
> 
VBoxManage modifyhd Win 7.vdi --resize 200000

But it won't accept the '7.vdi'

If the name of your vdi has a space in it, try putting the name in quotes so it is parsed as one parameter.

---

### Post by Kaizoku001 on 2011-10-14
this is what i get with the quotes:

>  VBoxManage modifyhd "Win 7.vdi" --resize 200000
VBoxManage: error: Could not find file for the medium '/home/papero/Win 7.vdi' (VERR_FILE_NOT_FOUND)
VBoxManage: error: Details: code VBOX_E_FILE_ERROR (0x80bb0004), component Medium, interface IMedium, callee nsISupports
Context: "OpenMedium(Bstr(pszFilenameOrUuid).raw(), enmDevType, AccessMode_ReadWrite, fForceNewUuidOnOpen, pMedium.asOutParam())" at line 210 of file VBoxManageDisk.cpp


And without.:
> VBoxManage modifyhd Win 7.vdi --resize 200000
Oracle VM VirtualBox Command Line Management Interface Version 4.1.2
(C) 2005-2011 Oracle Corporation
All rights reserved.

Usage:

VBoxManage createhd         --filename <filename>
                            --size <megabytes>|--sizebyte <bytes>
                            [--format VDI|VMDK|VHD] (default: VDI)
                            [--variant Standard,Fixed,Split2G,Stream,ESX]


Syntax error: Invalid parameter '7.vdi'


Any ideas?

---

### Post by teachop on 2011-10-14
I know this is a silly question but just in case...  Is that path correct?  My .vdi file is down two levels from my home directory.  For me it is ~/.VirtualBox/VDI/whatever.vdi so check and make sure you have the path right on the command line.

---

### Post by Kaizoku001 on 2011-10-14
> **teachop said:**
> I know this is a silly question but just in case...  Is that path correct?  My .vdi file is down two levels from my home directory.  For me it is ~/.VirtualBox/VDI/whatever.vdi so check and make sure you have the path right on the command line.
I tried that
here is what i got:
> papero@Kaizoku:~$ VBoxManage modifyhd /home/papero/VirtualBox VMs/Win7/Win_7.vdi --resize 200000
Oracle VM VirtualBox Command Line Management Interface Version 4.1.4
(C) 2005-2011 Oracle Corporation
All rights reserved.

Usage:

VBoxManage createhd         --filename <filename>
                            --size <megabytes>|--sizebyte <bytes>
                            [--format VDI|VMDK|VHD] (default: VDI)
                            [--variant Standard,Fixed,Split2G,Stream,ESX]


Syntax error: Invalid parameter 'VMs/Win7/Win_7.vdi'

the command just won't allow spaces. and when i us under bars instead it gives me an error message,

---

### Post by teachop on 2011-10-14
If you don't have quotes around it, a path with spaces gets parsed as two parameters.  Use quotes on the path.  No underscores unless they are really part of the pathname.

---

### Post by Kaizoku001 on 2011-10-14
Do i need " " or ' '.

#####edit#####

this is what I got:
> VBoxManage modifyhd "/home/papero/VirtualBox VMs/Win7/Win 7.vdi" --resize 200000
0%...
Progress state: VBOX_E_NOT_SUPPORTED
VBoxManage: error: Resize hard disk operation for this format is not implemented yet!


---

### Post by teachop on 2011-10-15
Looks like you got the command line correct that way, so that is progress.  The reason it doesn't resize is something to look up in the VirtualBox manual at this point.  I have resized my .vdi quite recently so I will look it up too, and see if I remember what I did.  I recall it was several steps.

---

### Post by Dakshinamurti on 2011-10-29
Diskresize with VirtualBox is fairly easy. Actually easier then posting this post here... 
:-)

You have to give as size parameter the total size of the new size, otherwise you might get the same error as if you'd have a total wrong disk format.

So we check first the current size of the disk-file in question:

```
VBoxManage showhdinfo <filename>
```When you get something like the following (Format VDI, Variant dynamic default) :
UUID:                 637eb924-ccd7-4779-a046-e3a0782d2815
Accessible:           yes
Logical size:         15360 MBytes
Current size on disk: 8526 MBytes
Type:                 normal (base)
Storage format:       VDI
Format variant:       dynamic default
In use by VMs:        test (UUID: 008f9c1b-4310-432a-942d-6710019a6c0d)
Location:             /home/vmdisks/Win7_32.vdi

then the resize is as easy as typing logoff... :-)

So, let's add 1GB of more diskspace (ok, makes no sense, but to show, it's enough)
That is: 15360MB + 1024MB = 16384MB

```
VBoxManage modifyhd Win7_32.vdi --resize 16384
```resulting with VBoxManage showhdinfo <filename>
UUID:                 637eb924-ccd7-4779-a046-e3a0782d2815
Accessible:           yes
Logical size:         16384 MBytes
Current size on disk: 8527 MBytes
Type:                 normal (base)
Storage format:       VDI
Format variant:       dynamic default
In use by VMs:        test (UUID: 008f9c1b-4310-432a-942d-6710019a6c0d)
Location:             /vmdisks/Win7_32.vdi

Ahaa!

But that's not all guys. In Win7, you've got to go now into systemmanager (right click on Computer, Manage), then diskmanager, and there you'll see the additional diskspace given. So yo've got to expand the current disk with that newly added space.
Don't know how XP will react, but I'm sure, you'll find out.

PS: blank spaces in either filename or somewhere in filesystem name is something unix's do not like much. So you've got to enclose them in quotes (single or double quotes) or mask the blank space with a \ (backslash).
I suggest, you take the quotes to enclose the whole thing.
Even better, never use space in either folders or filenames. :-)

---

### Post by lkraemer on 2011-10-30
You can also try:

VBoxManage modifyhd Win?7.vdi --resize 200000
VBoxManage modifyhd Win\ 7.vdi --resize 200000

lk

---

### Post by haqking on 2011-10-30
I never bother with any of that.

I just add another disk to the controller of a larger size then use clonezilla to clone it over to the new disk.

Then remove the old one as primary and remove it or use it as an additional disk in the OS

same as you would do in a physical system

---


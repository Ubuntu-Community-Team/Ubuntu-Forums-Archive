---
title: "Clean Ubuntu 16.04 install; getting &quot;No Bootable Device&quot; error on boot"
date: 2016-08-02
forum: Installation &amp; Upgrades
---

### Post by bsauer on 2016-08-02
Hi,

New to Ubuntu and the forums, and have run into a boot issue on a clean install of Ubuntu 16.04 onto a HP laptop.

Initially installed as a dual operating system install next to the Windows 8 OS.  As I didn't see an option to select Ubuntu on boot up, I did a cleared everything and did a clean install of 16.04.  At that point, allowing the boot process to continue I get to a "No Bootable Device" error.  Going into the BIOS, I can select Ubuntu and successfully load it.  However, I can't find any way to automatically have the boot process recognize the GRUB boot loader.

Steps taken so far:
1. Ran boot-repair on automatic settings. [No change]
2. Used gparted to set the boot flag on the Ubuntu partition /sda2. [No change]
3. Ran boot-repair on automatic settings again. [No change]

Here's the pastebin info file after my last attempt: [http://paste2.org/vm2O5wm5](http://paste2.org/vm2O5wm5)

Any help would be much appreciated -

Bryan

---

### Post by oldfred on 2016-08-02
You have an HP, that requires one of several work arounds as HP violates UEFI spec. It only allows boot by default of "Windows Boot Manager" by description.
But since you only have Ubuntu we can change description from ubuntu to Windows or have Windows description boot Windows.
Those that dual boot use the fallback or hard drive entry /efi/Boot/bootx64.efi. That usually is just a copy of Windows .efi file if you already have it. See line 14 in Summary report. You can also remove the existing Windows .efi files. (Edit - do not delete, see below as it now is shim).
But backup ESP partition sda1 before deleting anything.

You also are showing two ESP - efi system partitions. While UEFI may allow more than one, almost all implementations of UEFI only allow one. Use gparted or Disks and remove boot flag from sda2. (See line 62 in report).

It looks like Boot-Repair recognized you do not have Windows. Lines starting at 734.
```
 cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (& .grb)
df /dev/sda1
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb) 


```

The first is a copy of shim to bootmgfw.efi which we normally do not recommend anymore as Windows updates will convert it back to Windows boot. But with no Windows that will work.
The second copy is shim to bootx64.efi or the fallback boot entry, but you do not yet show a fallback boot entry.

System actually should now just boot the "Windows" description and actually boot into grub using grub's shimx64.efi.

Since no other system installed, you will not normally get grub menu. You may have to press escape immediately after UEFI on screen.

---

### Post by bsauer on 2016-08-03
Thanks for the response!

If I understood correctly, all you wanted me to do was remove the boot flag from sda2 with gparted [done], and Boot-Repair is already copying the shim files to replace the windows files.

Status:
- With no intervention on boot, goes to "No bootable device".
- If I go to the bios, I can select Ubuntu and boot it.

Any thoughts of what else I should try, or is this as good as I can get it?  Time to remove the windows files?

Here's the new output file:[  http://paste2.org/Dz7eBnJf]("http://paste2.org/Dz7eBnJf")

Thanks!!

---

### Post by oldfred on 2016-08-03
If you choose the Windows entry does it boot into Ubuntu? It should as it reported shim was copied to Windows bootmgfw.efi. And that is what UEFI is booting.

Do you have secure boot off? Report says it is off. But error you are getting is more common with Secure boot on.

One user reported his HP UEFI did have additional settings buried somewhere that allow Ubuntu boot.
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file) 

You can also add the hard drive or fallback boot entry and see if you can set it as default.
      
 sudo efibootmgr -c -g -d /dev/sd[COLOR=#ff0000]X[/COLOR] -p [COLOR=#ff0000]Y[/COLOR] -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition  
OR:
sudo efibootmgr -c -g -d /dev/sda -p 1 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
Since your ESP is sda1.

For single installs of Ubuntu with no Windows we normally change the UEFI entry rather than copy shim to bootmgfw.efi. Then you do not need the /EFI/Microsoft folder in ESP.

 If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by bsauer on 2016-08-05
All right, its working.  Thanks for pointing me in the right direction.

I did find additional configuration requirements in the bios thanks to the HP UEFI thread you sent.  Ultimately I needed to:

1. Go to boot configuration
2. Add a "Customized Boot"
3. Point "Customized Boot" to \EFI\ubuntu\grubx64.efi
4. Change UEFI boot order with "Customized Boot" on top.

...and then it booted to Ubuntu without intervention.

Anyways: it works!  Thanks for the help!

---

### Post by oldfred on 2016-08-05
Glad you got it working. 
And good to know HP now has the customized boot option at least on some computers.

Please change to Solved.

---


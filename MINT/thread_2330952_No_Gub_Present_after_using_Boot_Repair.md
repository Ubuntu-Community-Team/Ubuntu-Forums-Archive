---
title: "No Gub Present after using Boot Repair"
date: 2016-07-16
forum: MINT
---

### Post by SuperFreak on 2016-07-16
I am in a jam. I have a dual boot of Mint 18 cinnamon edition and 16.04. I was trying to make Mint the first OS in the grub menu and thought Boot Repair would do that and I now have no Gub.
While using Boot repair I was told to issue the command sudo apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic

This is what happened.

```
david@MainSqueeze ~ $ sudo apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 linux-signed-generic : Depends: linux-headers-generic (= 4.4.0.31.33) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
david@MainSqueeze ~ $ sudo update-grub
sudo: update-grub: command not found
david@MainSqueeze ~ $ 

```

How do I restore Grub?

Here is my recent Boot Repair Report [http://paste2.org/pLbjnOe8](http://paste2.org/pLbjnOe8)

Also
```
$ uname -r
4.4.0-28-generic

```


EDIT: I reran Boot Repair and disabled the option for Secure Boot in advanced settings and now it works fine.Whew!

---

### Post by DuckHook on 2016-07-17
It seems that you don't have linux-headers-generic installed. This has happened before to me on some installs but it is still odd because the header files are an important part of your system. You may encounter other problems, usually when you are trying to install apps, unless you install these headers. You should also always do:```
sudo apt update
```...before trying to install anything. In your case I would then suggest:```
sudo apt install linux-headers-generic
```...irrespective of whether you can now boot.

---

### Post by SuperFreak on 2016-07-17
Thanks

I now have the headers installed but uname -r says

```
~ $ uname -r
4.4.0-28-generic

```

---

### Post by oldfred on 2016-07-17
You have grub also installed to gpt's protective MBR for BIOS boot, but have an UEFI install.
For BIOS install of grub you have to have a bios_grub partition which you do not. So install is UEFI.

So did you change boot mode to BIOS/CSM/Legacy in UEFI? 
Change back to UEFI.

---

### Post by SuperFreak on 2016-07-17
> **oldfred said:**
> You have grub also installed to gpt's protective MBR for BIOS boot, but have an UEFI install.
For BIOS install of grub you have to have a bios_grub partition which you do not. So install is UEFI.

So did you change boot mode to BIOS/CSM/Legacy in UEFI? 
Change back to UEFI.

Thanks
On another forum it was suggested that I use Grub Customizer and select the option "Install to MBR". I did not realize that would install grub to MBR. Should I uninstall it and how?

I believe I am in EFI mode

```
 $ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

EFI boot on HDD

```

[http://paste2.org/JOCV42nY]("http://paste2.org/JOCV42nY")

---

### Post by oldfred on 2016-07-17
While some like & use Grub Customizer, I have seen others with issues. It adds its own scripts to modify many things. Often just a few settings need to be changes and that can be easier to do.

You can and probably should just use Boot-Repair and run its full uninstall/reinstall of grub2. That will remove the custom scripts.

While you can use dd to erase the part of the protective MBR with boot code, use of dd can be very dangerous. I suggest leaving code there, as it is never used, but never set UEFI to boot in BIOS mode as then it tries to use that broken code.

---

### Post by SuperFreak on 2016-07-17
Thanks OldFred. I ran boot repair again and it updated the kernel to 4.4.0.31 so that issue was resolved

---


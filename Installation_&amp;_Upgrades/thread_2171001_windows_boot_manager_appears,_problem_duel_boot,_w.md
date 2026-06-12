---
title: "windows boot manager appears, problem duel boot, win8 / ubuntu 12.04"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by whitey_1 on 2013-08-28
Hi everyone,

I have recently bought a new HP laptop, with the dreaded windows 8 pre installed. Naturally, I went to install ubuntu 12.04 in a duel boot.

I ran the installation and went along with the standard settings, i didnt make any adjustments. When i went to restart the pc, there was no grub loader giving me the option of loading either OS, instead windows 8 loaded as it did before.

I then restarted again but pressed ESC to choose ubuntu from a 'boot manager' list, which then gave me the grub loader.

I would rather have the grub loader come up straight away after starting the laptop. 

I then went back to windows and installed something called EasyBCD to give me the options to make adjustments to the boot order. I then went to try and create a new boot order, ive tried all the ones that are offered, and none of them work apart form the windows 8 option.

Can someone help with this? i just want grub loader to load without all this other nonsense 

Thank you

---

### Post by carl4926 on 2013-08-28
Do you even need windows at all?

---

### Post by whitey_1 on 2013-08-28
yeah i do for my studies, because there is a chance I will need to use some software that can only be used on windows.

---

### Post by carl4926 on 2013-08-28
And you don't have a windows install DVD?

I know Jack All about [COLOR=#000000]EasyBCD
Except it causes problems

You did follow this? [/COLOR][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
With you Ubuntu install?

---

### Post by oldfred on 2013-08-28
With UEFI you should not need EasyBCD. With BIOS a few users preferred to boot Windows most of the time and used it.

If you set in the UEFI/BIOS menu boot order and make Ubuntu first it should always boot. But did you install Ubuntu in UEFI mode, not BIOS mode? If not in same mode you have to always go into UEFI to boot. Boot-Repair can convert a BIOS install to UEFI.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by whitey_1 on 2013-08-28
No they dont supply the discs with windows any more, it comes already installed.

Easybcd doesnt seem too bad to me, I can choose so that the laptop behaves like it was before installing linux.

Thanks for the link, but i think that those instructions look quite risky, im not sure i want to make changes without knowing what they all mean.

---

### Post by whitey_1 on 2013-08-28
Thanks Fred, 

I began looking at the link .. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

it  says to start by putting the ubuntu cd in and running with the option  of trying ubuntu without installing it. When it loaded, i went to the  terminal and entered:
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

I entered that, and it returned with an error messege. The last line of the error message reads:
pycurl.error: (6 "couldnt resolve host 'launchpad.net'")

Do I actually have to use the linux cd? as i have it already installed on my laptop

---

### Post by whitey_1 on 2013-08-28
quick update .. i loaded ubuntu and entered 
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

it didnt have the error message this time

I then entered:
sudo apt-get install -y boot-repair && boot-repair

Then a window came up saying .. boot repair, EFI detected. Please check the options

??

---

### Post by whitey_1 on 2013-08-28
OK more messages have come up now. It says to deactivate securebot .. and it says there is a buggy kernal

i hope someone knows about what this all means or else im getting myself into more trouble

---

### Post by whitey_1 on 2013-08-28
ok here we go .. i used the boot repair program, and it says that i have to copy the following URL to my favourite  support forum :D

[http://paste.ubuntu.com/6038071/](http://paste.ubuntu.com/6038071/)

i hope that makes some sense to someone, because im in trouble here, i got no idea what im doing, so i dont want to be stabbing around in the dark causing myself more problems

can anyone help with this problem

---

### Post by oldfred on 2013-08-28
I can see you never installed Ubuntu in BIOS mode which is good.

And it now shows the secure boot versions of the kernel installed, so you can boot with secure boot on. Only a few systems are hard coded to only boot Windows efi file. If you cannot choose to boot Ubuntu from UEFI menu with secure boot on or off, then you may have to use a rename function. But it should work now.

Also HP puts a lot of efi files in the efi partition. Boot-Repair adds them all to grub menu. You may not want all of them and can backup and edit. Details in link in my signature on manually editing 25_custom.

---

### Post by whitey_1 on 2013-08-28
I followed the instructions for disabled secureboot , then i went to restart, i then restarted and there is now no option for starting windows.

It seems like things have now got a lot worse.

---

### Post by oldfred on 2013-08-28
You must have one of the systems that will only boot Windows with secure boot on. Did UEFI show Ubuntu? 
Both Windows & Ubuntu should boot with secure boot off.

When you have secure boot on, it will only show systems that are secure boot as boot options.

---

### Post by ubfan1 on 2013-08-28
Looks like you have a secure boot setup, you just lack having ubuntu (the shim entry) in the bootorder.  Look at the pastebin output around line 498.  use efibootmgr to change the bootorder, putting 0000 first.

---

### Post by whitey_1 on 2013-08-29
All that happens now is, when i start the laptop it takes me to a menu saying ' windows boot manager ' and then gives me 2 options, both saying ' neosmart linux ' if i choose either of these then it reports an error message ' windows failed to start ..... '

There is no windows boot option now. 

If i press ESC then i am taken to another ' boot manager ' where i have 4 options .. OS boot manager , Ubuntu (hitachi ....) , ubuntu (hitachi ....) , boot from EFI file ...

I have been trying boot from efi .. i got no idea what i am doing though.

---

### Post by oldfred on 2013-08-29
You have/had Windows set as default from UEFI and see the EasyBCD boot menu. That is not the UEFI boot menu. 

The second menu you posted, is the UEFI boot menu and in UEFI you can also change default to ubuntu.

You also should have a one time boot key which lets you boot another option just once. Then you can directly boot Windows or flash drive as test or repair without having to change boot order in UEFI.

 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---


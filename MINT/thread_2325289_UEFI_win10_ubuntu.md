---
title: "UEFI win10 ubuntu"
date: 2016-05-20
forum: MINT
---

### Post by pdc on 2016-05-20
so with a second-hand HP Pavilion running Win10, I successfully installed alongside the existing Win10 ...actually it is Mint but the Ubuntu forums is tops! The linux install runs well; the only way I can get it so far is F9 as the laptop boots; scroll down to press what is called Ubuntu which is below the OS boot option; can any kind soul guide me on attempting to give myself a screen after booting that shows the linux option please...........happy to supply any other data needed

---

### Post by oldfred on 2016-05-20
Moved to Mint.

Is system UEFI?

Run Boot-Repair, it copies shim to /EFI/Boot/bootx64.efi which is a harddrive or fallback boot entry that you then can use.
If your system does not have to Hard drive boot entry we can add one.

       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Manually copy files.
       HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 
           
         Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
    [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by pdc on 2016-05-21
thanks very much oldfred: delighted to see your reply; 

I have the Mint open on the hard drive: so if I run the second option from here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) from the Mint partition?

I didn't understand in the second paragraph when you said 
"Manually copy files.
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
http://ubuntuforums.org/showthread.php?t=2131886"

.......... did I have to do all those components of your reply: ........... can I just run the first option with boot-repair; reboot and see where things are at?

____

"Is system UEFI?"

......not sure what the defn of that is: we set up legacy mode in the F10 boot options; and disabled secure boot: the windows diagnostics EasyBCD says it is still running in EFI mode

_________

I did download and install boot-repair; and run it; shall I paste the result here?

---

### Post by yancek on 2016-05-21
Paste the link to boot repair here as it doesn't do any good wherever it is now.  How does EasyBCD fit into this picture?  The boot repair output will tell if it is UEFI or not.

---

### Post by oldfred on 2016-05-21
Boot-Repair should do the copy of shimx64.efi into /EFI/Boot as bootx64.efi.

Summary report after you run it will show it did it.
Although Windows efi boot file is often already bootx64.efi & Boot-Repair will just back that up & rename it.
Use the Standard efi boot file option.

[https://bugs.launchpad.net/ubuntu/+bug/1531178](https://bugs.launchpad.net/ubuntu/+bug/1531178)


The links to manually doing it is if you do not have or want Boot-Repair. Or want to learn to use command line. Or the old way to do it.

---

### Post by pdc on 2016-05-21
My apologies for not including the paste earlier [http://paste2.org/DnMeK3Ut](http://paste2.org/DnMeK3Ut)

thanks to you for commenting; if I await your comments before any further actions here

______________

1) when I search in the pastebin, it seems to me to say that [COLOR="#B22222"]/boot/efi/EFI/ubuntu/shimx64.efi[/COLOR] was successfully copied to [COLOR="#EE82EE"]/boot/efi/EFI/Boot/bootx64.efi so that is good
[/COLOR]
2) at the end of the pastebin, I see > If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
[COLOR="#FF0000"]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi[/COLOR]

as I can currently get into linux mint on the HP by tapping F9; then scrolling down one from OS Boot Manager to what is Mint and then hitting enter; if I carry out the above advised action of running the command in win10?

---

### Post by oldfred on 2016-05-21
Do you have a hard drive entry or fallback. (UEFI not BIOS). 
And can you set that as default boot to get into Mint. It was not shown in report, but UEFI may add it on reboot.
If not we can add one, that you then should be able to set as default boot.

You should be able to directly boot Windows from your one time boot key f9.
The edit of BCD is another work around. Some find that ok, but I believe you have to boot into Windows and it then totally reboots using UEFI's one time reboot to boot Ubuntu.

You show two efi partitions. Many systems have huge issues with that.
Remove boot flag from sda4 with gparted or other tools.
With UEFI/gpt the boot flag can only be on the ESP - efi system partition that has the .efi boot files.
It is not the same as a boot flag with BIOS/MBR where it indicates which partition has Windows boot files. Grub does not use boot flag.

---

### Post by pdc on 2016-05-21
> Do you have a hard drive entry or fallback. (UEFI not BIOS).  I am sorry: I don't know what that means. 

> And can you set that as default boot to get into Mint. It was not shown in report, but UEFI may add it on reboot. I would like to have Mint as default boot; however the HP repeatedly just boots into Win: only by pressing F9 and selecting second on list: Mint, can I boot Mint

to reaffirm: the laptop by itself boots straight into Win; by selecting F9 at startup, and then selecting Mint, it boots well to Mint;

> If not we can add one, that you then should be able to set as default boot.that would be great

> You should be able to directly boot Windows from your one time boot key f9..........indeed it works fine

> The edit of BCD is another work around. Some find that ok, but I believe you have to boot into Windows and it then totally reboots using UEFI's one time reboot to boot Ubuntu..........do you mean EasyBCD? It says Win is in EFI so I cannot do what this youtube clip suggests I should be able to do: [https://www.youtube.com/watch?v=vxepmtjmilQ](https://www.youtube.com/watch?v=vxepmtjmilQ) at the time point 11.20; and that is edit the boot menu

> Remove boot flag from sda5 with gparted or other tools. I removed the boot flag from sda5; closed gparted; restarted; and again it just loads windows

---

### Post by oldfred on 2016-05-21
Do not use EasyBCD to boot with. I do not know all its functions, but it may also be a Windows repair disk.

HP violates UEFI spec and uses description as part of its UEFI boot. And of course only valid description is "Windows Boot Manager". 
But all UEFI boot a fallback or hard drive entry. 

Run this:
sudo efibootmgr -v

You will see both Windows & Ubuntu as UEFI boot entries. We will add another that is Hard drive but UEFI, not BIOS.

```
 Notebook Hard Drive BIOS
Boot0005* Windows Boot Manager    HD(3,121800,31800,968f6a14-c74f-487d-83db-b11149e2452c)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS......
Boot0006* ubuntu    HD(3,121800,31800,968f6a14-c74f-487d-83db-b11149e2452c)File(EFIubuntushimx64.efi) 


```

       sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "Notebook Hard Drive UEFI" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition  

So your entry is for sda and partition 3:
sudo efibootmgr -c -g -d /dev/sda -p 3 -w -L "Notebook Hard Drive UEFI" -l '\EFI\Boot\bootx64.efi' 

rerun:
sudo efibootmgr -v
And you should see your new entry.
It should boot with your f9, best to test first, but I think it may let you set that as default or first in boot order in UEFI.

Details on efibootmgr parameters:
 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by pdc on 2016-05-21
thanks very much; as you advised I ran the command "[COLOR="#EE82EE"]sudo efibootmgr -v[/COLOR]" and then "[COLOR="#EE82EE"]sudo efibootmgr -c -g -d /dev/sda -p 3 -w -L "Notebook Hard Drive UEFI" -l '\EFI\Boot\bootx64.efi'[/COLOR] " and then "sudo efibootmgr -v"again and I got the result

> sudo efibootmgr -c -g -d /dev/sda -p 3 -w -L "Notebook Hard Drive UEFI" -l '\EFI\Boot\bootx64.efi' 
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0006,0005,3005,0001,2001,2002,2003
Boot0000* Internal EFI Shell
Boot0001* ubuntu
Boot0002* Notebook Hard Drive
Boot0003* Network Adapter (IPv4 Legacy)
Boot0004* Internal EFI Shell
Boot0005* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot3005* Internal Hard Disk or Solid State Disk
Boot0006* Notebook Hard Drive UEFI

....... closing Mint and rebooting, win opened with no prompt screen; rebooting from win and pressing F9 gave the old order: OS Boot Manager and Mint as number 2; and Mint still boots fine from there

_____________________________

when I look back to your previous post, you included in code a whole lot of data: I assumed that was just illustrative .............

---

### Post by oldfred on 2016-05-21
Does the new entry work to also boot Mint?
The efibootmgr entry shows 0006 as first in boot order. It it also that way in UEFI's boot tab?

Most go into UEFI and change boot order there. And Windows may change order on its own with updates.

You also can change boot order with efibootmgr. 

       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
sudo efibootmgr -o 6,1,5

---

### Post by pdc on 2016-05-22
> Does the new entry work to also boot Mint? ..........no.....on startup it loads windows

> The efibootmgr entry shows 0006 as first in boot order. [COLOR="#FF0000"]It it also that way in UEFI's boot tab?[/COLOR]........don't know how to answer that; 

> Most go into UEFI and change boot order there. And Windows may change order on its own with updates..........thanks; will check how to go into UEFI to look at boot order there

> sudo efibootmgr -o 6,1,5  thanks; I will read on what you raise above and then try the command you recommend; 

many thanks for your continuing support

---

### Post by pdc on 2016-05-22
so I rang the command > 

and the result was 

> BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0006,0001,0005
Boot0000* Internal EFI Shell
Boot0001* ubuntu
Boot0002* Notebook Hard Drive
Boot0003* Network Adapter (IPv4 Legacy)
Boot0004* Internal EFI Shell
Boot0005* Windows Boot Manager
Boot0006* Notebook Hard Drive UEFI
Boot2001* USB Drive (UEFI)
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot3005* Internal Hard Disk or Solid State Disk

when I reboot, the HP persists in just loading WIN: no other options loaded; 

in this link [http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr) the answer suggested the command that Boot Repair suggested, namely > bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi.........this person adds "([COLOR="#EE82EE"]If you've disabled Secure Boot, you can replace shimx64.efi with grubx64.efi, although either should work with Secure Boot disabled.[/COLOR])"

should I also run this command from within WIN?

_________________

to WIN, I downloaded a utility called EasyUEFI; I moved ubuntu up the boot order to the top: as hopefully shown on the screenshot; despite that, the computer boots to WIN without any other options

---

### Post by oldfred on 2016-05-22
Yes, BCD is Windows boot file. It normally shows other Windows, but you can add the Ubuntu entry.

You did not post the efibootmgr -v which also shows the details of the boot option.
Does HP have an internal command that shows /EFI/Boot/bootx64.efi. I have seem some Boot-Repair reports that show that.
But most of the other UEFI entries you posted before were for BIOS or external devices.

Otherwise the only option is the edit BCD.

---

### Post by pdc on 2016-05-22
[HTML]BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0005,3005,0001,0006,2001,2002,2003
Boot0000* Notebook Hard Drive	BIOS(2,500,00)................-.V.......V.A.V.............................................A.................... ...
Boot0001* ubuntu	HD(3,121800,31800,968f6a14-c74f-487d-83db-b11149e2452c)File(\EFI\ubuntu\shimx64.efi)
Boot0002* Network Adapter (IPv4 Legacy)	BIOS(80,0,00).......................................................................
Boot0003* Internal EFI Shell	MM(b,b9e45010,ba64500f)RC....
Boot0004* Internal EFI Shell	MM(b,b9e45010,ba64500f)RC....
Boot0005* Windows Boot Manager	HD(3,121800,31800,968f6a14-c74f-487d-83db-b11149e2452c)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...o............. ...
Boot0006* Notebook Hard Drive UEFI	HD(3,121800,31800,968f6a14-c74f-487d-83db-b11149e2452c)File(\EFI\Boot\bootx64.efi)
Boot2001* USB Drive (UEFI)	RC
Boot3002* Internal Hard Disk or Solid State Disk	RC
Boot3003* Internal Hard Disk or Solid State Disk	RC
Boot3005* Internal Hard Disk or Solid State Disk	RC
Boot3006* Internal Hard Disk or Solid State Disk	RC[/HTML]

my apologies for not posting the result of "efibootmgr -v" and I have posted it above

"[COLOR="#008000"]Does HP have an internal command that shows /EFI/Boot/bootx64.efi[/COLOR]." .............gosh, I don't know: can you suggest how I would check that out?

---

### Post by oldfred on 2016-05-22
It is showing 0005 as default again.And 3005 as second choice? Something changed that from the 6,1,5 we set with efibootmgr. Or it did not really save that.

We added the 0006, I was wondering if HP had seen the /EFI/Boot/bootx64 and added its own boot. Does not look like it has.

What does the 300x entries do?
They may go into HP's own recovery??

Does 0006 when manually booting work ok?
While efiboot manager should re-order default boot entries, does it show the same in UEFI? 
Not sure with HP, but most have a boot tab where you also select which system to boot, usually just simple description so sometimes hard to tell which is which.

---

### Post by pdc on 2016-05-22
so I ran the command "[COLOR="#EE82EE"]sudo efibootmgr -c -g -d /dev/sda -p 3 -w -L "Notebook Hard Drive UEFI" -l '\EFI\Boot\bootx64.efi'[/COLOR] " again; and changed the boot order to 6,1,5 but on rebooting we have "0005, 3005, 0001, 0006, 2001, 2002, 2003"

"[COLOR="#0000FF"]What does the 300x entries do?[/COLOR]" ...........I am guessing that is rhetorical: I don't know

"[COLOR="#0000FF"]Does 0006 when manually booting work ok?[/COLOR]" .........don't know: how should I test this?

"[COLOR="#0000FF"]While efiboot manager should re-order default boot entries, does it show the same in UEFI?[/COLOR]"     ..........don't know: could you advise how to check this please

"[COLOR="#0000FF"]Not sure with HP, but most have a boot tab where you also select which system to boot, usually just simple description so sometimes hard to tell which is which[/COLOR]. " ..not sure where I should be looking for all of this: I enclose a shot of what the F9 shows on bootup: it is unchangable, through thick and thin

___________

in post #9, you showed text inside code markers; I have never been clear: was that an example or was I to somehow use and paste it in somewhere

---

### Post by oldfred on 2016-05-22
Not f9 but actual UEFI.
It has many settings, but should have a boot tab where you choose boot order.
On my Asus it is on this screen but I have to scroll down to find the boot order settings.

I thought Boot-Repair automatically changed bootx64.efi but in re-reading you may have to choose an option.
       
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)

---

### Post by pdc on 2016-05-22
"[COLOR="#0000FF"]Not f9 but actual UEFI[/COLOR]." ...........I followed this HP guide to attempt to access UEFI firmware settings: [http://support.hp.com/nz-en/document/c03801890](http://support.hp.com/nz-en/document/c03801890) and I get what is shown in the screenshot; 
________

"[COLOR="#0000FF"]I thought Boot-Repair automatically changed bootx64.efi but in re-reading you may have to choose an option.

Boot-Repair now creates bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options[/COLOR]."

in advanced options in BootRepair, this is the screen I get: should I run this with options set as is ....

---

### Post by oldfred on 2016-05-22
I do not have Boot-Repair on this computer yet. But I believe you just have to make sure that option is checked.

I do not see a screen shot of your UEFI or were you referring to my screen shot. And HP link does not work for me.
What is boot order in UEFI then?

---

### Post by pdc on 2016-05-22
my apologies: screenshot now added

for attempting to access UEFI I did the restart: advanced options; troubleshooting; UEFI firmware settings; restart was the sequence I believe

---

### Post by pdc on 2016-05-22
"I do not have Boot-Repair on this computer yet. But I believe you just have to make sure that option is checked."         on the screenshot of advanced options for BootRepair, there are several options: eg "Reinstall GRUB" and "Restore EFI backups", as well as the "Use the standard EFI file": do I just let BootRepair run with all its default options ticked; in the advanced mode?

You could not access the HP website on how to get into the UEFI bios: this Acer instruction is as I did [http://acer.custhelp.com/app/answers/detail/a_id/37064/~/windows-10%3A-access-the-uefi-bios](http://acer.custhelp.com/app/answers/detail/a_id/37064/~/windows-10%3A-access-the-uefi-bios)

---

### Post by oldfred on 2016-05-22
I would then just tick "Use the Standard file".
The restore is to undo changes that Boot-Repair did, which may be just the opposite of Use the Standard file.

And reinstall grub is for major issues to houseclean corrupted files. Or to convert from/to UEFI or BIOS.

---

### Post by pdc on 2016-05-22
BootRepair takes away the option to "use the standard EFI file" when one disables the "reinstall GRUB" button

---

### Post by pdc on 2016-05-22
you must be getting weary of all of this; the laptop is a friend's who wanted to try linux: it will start linux reliably by just pressing F9; then select Mint and then clicking on Mint in the grub screen that then appears; I think he is up to that; I can only hope he finds linux good enough to ditch win in a little while and we can then just do a clean linux install on the whole disc

---

### Post by oldfred on 2016-05-22
Wish I knew HP better, but know most have had issues.

As long you you want help I am here, but running out of ideas.

---

### Post by pdc on 2016-05-22
well if we just leave it as it is: I was enormously grateful when I posted for help to see you reply: and continuously grateful as you made suggestion after suggestion; I will leave it as is: return the laptop; and then show my colleague how to use the linux; 

many thanks again for all your help and support

---

### Post by oldfred on 2016-05-22
Glad I could help. 
Wish it was totally correct, but a few users prefer the one time boot key or f9 way to choose which to boot.

---

### Post by Lancro on 2016-05-25
I had this issue, and I did sudo update-grub in a terminal, all solved, dont know why noone has tried this, windows 10, UEFI as well, Linux Mint Cinnamon 17.3, worked perfectly, menu appeared and I can boot on both systems.

---

### Post by pdc on 2016-05-25
thanks; I returned the computer yesterday; I will suggest this to them

---


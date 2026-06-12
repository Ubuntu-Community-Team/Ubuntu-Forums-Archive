---
title: "dual boot xubuntu windows 7 problem"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by gennarof on 2015-08-19
trying to have dual boot xubuntu 14.04 LTS and  windows 7 <work reasons : (
new computer laptop acer E5-571-57H1
windows 7 pre installed (not used at all, just opened)
UEFI
Secure Boot disabled
windows starts automatically, F12 does not list xubuntu
tried secure boot repair - no luck
tried boot into Windows admin command prompt: bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi - no luck
here secure boot repair report [http://paste.ubuntu.com/12125054/](http://paste.ubuntu.com/12125054/)
if somebody could help, many thanks

---

### Post by oldfred on 2015-08-19
It looks like you left Windows fast startup on. You need to have that off.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Acer do not need the suggested fix by editing BCD in Windows.
But they need you to set a supervisory password and set "trust" on the Ubuntu boot files.
       
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

---

### Post by gennarof on 2015-08-20
Many many thanks Oldfred and for the very quick reply
I am a 9 years passionate ubuntu user and I never found such a complicate issue
it took me 8 hours to solve (for sure my skills do not help...)
I am surprised that Acer created such a ridiculously complicates setting, microsoft is not enough, we need also the manufacturers messing around...

I solved through these links
[URL="http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044"]http://ubuntuforums.org/showthread.p...4#post13203044
[/URL][http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

not sure turn off windows fast start-up necessary
for sure not necessary disable Secure Boot in bios in my case <a lot of advice stress the importance of this

I try to recap my solving (for computer laptop acer E5-571-57H1)
(after installed xubuntu)

turn on and press F2, bios come up (mine called InsydeH20 setup utility rev. 5.0)
go to page Security
go to "Set Supervisor Password" press ENTER (I set pass "a")
go to "Select an UEFI file as trusted for executing:" press ENTER
a new page appear with listed:
HDD0
HDD0

press ENTER on the first HDD0 and see if a sub list with the name "<EFI>" comes up (in my case did not show <EFI> but: recycle bin and system volume info)
press ENTER on the second HDD0 and see if a sub list with <EFI> comes up (in  my case showed <EFI> and <boot-sav>)
press ENTER on <EFI>, new list comes
press ENTER on<ubuntu>, new list comes with:
shimx64.efi
grubx64.efi
MokManager.efi

press enter on each one and give them a for you recognizable name (I used "xubuntushimx64efi", "xubuntugrubx64efi", "xubuntuMokManagerefi")
and press Yes

save and exit

go back in bios f2

go to "Set Supervisor Password" and set pass to nill-blank (you want to eliminate a not necessary password that you could forget...)

go to "boot page" tab
you should find the named shimx64.efi, grubx64.efi, MokManager.efi
bring them up in the priority boot list (above windows if you want ubuntu default system)

go to page main - enable F12 boot menu
save and exit

now ubuntu should be your main boot and if you need windows press F12 at start and select...

madness!!!!!

---


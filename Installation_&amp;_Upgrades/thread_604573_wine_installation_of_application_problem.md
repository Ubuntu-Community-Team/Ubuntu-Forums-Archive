---
title: "wine installation of application problem"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by g.a. on 2007-11-06
Hi,

I'm using kubuntu 7.04 and installed wine 0.9.33

when trying to install a windows software (for fantasy soccer...) I got the errors below. this is the very last windows application i use:

gianluca@neo:~$ wine fcm822.exe
fixme:reg:GetNativeSystemInfo (0x34fea0) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x34fe9c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x16a420 0x34fe1c) stub!
fixme:sfc:SfcIsFileProtected ((nil), L"Z:\\home\\gianluca\\%SystemDrive%\\Program Files\\FCM\\FCM.exe") stub

any suggestion?

---

### Post by ROBarber on 2007-11-06
make an update for wine

apt-get install wine (with sudo if you are not root).

it seems that sfc.dll is not pointed well to the windows os (emulates for xp).

for your information you can visit [http://www.winehq.org]("http://www.winehq.org")

good luck

---

### Post by g.a. on 2007-11-07
thanks a lot for your reply. i have installed the version 0.9.48 for ubuntu.

still the installation does not seem to work. i run the installing exe, it does its stuff and exit telling the installation was succesfull. however, there is not exe nowhere in my hard disk...

the wine installation seems to be correct since i can run some sample application such as windows notepad. 

here is the output when installing my application.


gianluca@neo:~$ wine fcm822.exe
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
fixme:winspool:AddPrinterDriverExW Flags 0x8 ignored (Fallback to APD_COPY_ALL_FILES)
fixme:winspool:AddPrinterDriverExW ### DrvDriverEvent(...,DRIVEREVENT_INITIALIZE) not implemented yet
fixme:reg:GetNativeSystemInfo (0x34fea0) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x34fe9c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x12da38 0x34fe1c) stub!
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Program Files\\FCM\\FCM.exe") stub

any suggestion?
thanks
g.

---


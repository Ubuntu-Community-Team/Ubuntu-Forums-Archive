---
title: "Need help installing iTunesSetup.exe with wine"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by robsquared on 2009-12-26
Following the instructions on Ubuntu's website, I thought I successfully installed wine:

computer@desktop-050909:~$ winecfg
wine: created the configuration directory '/home/computer/.wine'
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cf24
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x20190c (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa82e8d8, overlapped 0xa82e8e0): stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x2042084 (nil)
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/computer/.wine' has been updated.
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory


I did get the Configure Wine window, as expected, and have set my default to Windows 7.

I also sucessfully downloaded the iTunesSetup.exe file and saved it to my desktop, but when I try to install it, I get the following:

computer@desktop-050909:~$ wine iTunesSetup.exe
wine: Module not found


PLEASE HELP!

---

### Post by phillw on 2009-12-26
Hi,

a few folks have said that the latest beta of Wine is running better than the stable one ..

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Depending on what you want to do with your iphone, there are also a couple of ubuntu resources for syncing etc.

If you pop in > iphone ubuntu +9.10 into google, it'll give you various options, including virtualisation (where you run windows from within Ubuntu)

Have fun exploring.

Remember, when you're installing programmes, they quite often say ```
sudo su
```This is not *really* the best way, it is better to instead use ```
sudo
``` before the commands - It will ask you for your password once, then allow you to issue **sudo** commands for about 10 minutes without re-asking you.

Whichever way you do it - be careful, both sudo and sudo su remove the safe-guards from Ubuntu - If you make a typo, you can kill your system.

Regards,

Phill.

---

### Post by robsquared on 2009-12-26
I believe I did install the Beta version of Wine (wine 1.2).

---


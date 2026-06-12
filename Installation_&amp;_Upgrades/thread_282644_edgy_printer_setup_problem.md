---
title: "edgy printer setup problem"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by muusikko on 2006-10-23
When I tried to install brother cupswrapper driver (from brother linux support page) there comes an error message:
"lpadmin: Unable to copy PPD file!"

I tried also manyally same command I found in the script /usr/local/Brother/cupswrapper/cupswrapperDCP7010-1.0.1 

"sudo lpadmin -p DCP7010 -E -v usb:/dev/usb/lp0 -m /usr/share/cups/model/DCP7010.ppd"

but it doesn't work, same error comes.


The solution was to copy /usr/share/cups/model/DCP7010.ppd to /etc/cups/ppd.

The driver install worked perfect with Dapper. Is this a problem with lpadmin or brother driver script? If the lpadmin is command wrong, why it worked with Dapper?

---

### Post by muusikko on 2006-10-23
Just after a couple of minutes I sent a message, I found what's wrong..

I checked out /var/log/cups/error_log

E [23/Oct/2006:09:16:39 +0300] CUPS-Delete-Printer: Unauthorized
E [23/Oct/2006:09:16:46 +0300] CUPS-Add-Modify-Printer: Unauthorized
E [23/Oct/2006:09:16:46 +0300] copy_model: empty PPD file!
E [23/Oct/2006:09:16:46 +0300] PID 6227 (/usr/lib/cups/daemon/cups-driverd) stopped with status 1!
E [23/Oct/2006:09:16:46 +0300] [cups-driverd] Unable to open "/usr/share/ppd/DCP7010.ppd" - No such file or directory
E [23/Oct/2006:09:24:06 +0300] CUPS-Add-Modify-Printer: Unauthorized
E [23/Oct/2006:09:25:22 +0300] CUPS-Add-Modify-Printer: Unauthorized
E [23/Oct/2006:09:25:22 +0300] copy_model: empty PPD file!
E [23/Oct/2006:09:25:22 +0300] PID 6576 (/usr/lib/cups/daemon/cups-driverd) stopped with status 1!
E [23/Oct/2006:09:25:22 +0300] [cups-driverd] Unable to open "/usr/share/ppd/DCP7010.ppd" - No such file or directory


after " sudo cp /usr/share/cups/model/DCP7010.ppd /usr/share/ppd/" everything works fine.

/usr/local/Brother/cupswrapper -script should copy the ppd file to /usr/share/ppd, not /usr/share/cups/model/.

Have the cups directories been changed in Ubuntu Edgy or something else? Because it worked in Dapper without problems.

---


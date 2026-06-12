---
title: "Set Default Printer with script"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by futura84 on 2012-04-02
I have a small company and am currently exploring the possibilities of renewing all my hardware, which is becoming outdated. I want to run a centrally managed ubuntu desktop, onto which my employees can connect over RDP with thin clients. That is all up and running (through xrdp), however, I have one issue with printers.
 
I have experimented with using Windows Server 2008, as it has the ability to assign printers to users based on IP-address or computername through the Group Policy editor (ref: [http://www.grouppolicy.biz/tag/printer/](http://www.grouppolicy.biz/tag/printer/) ). However, there are also some third party apps that will do this, like SetDefaultPrinter (ref: [http://12.mayjestic.net/index.php/20080330/tool-for-setting-default-printers-on-users-local-remote-computernames/](http://12.mayjestic.net/index.php/20080330/tool-for-setting-default-printers-on-users-local-remote-computernames/) ). This is very handy for me, as my employees constantly move between thin clients at the office; it would be unfeasible to instruct them to always change their default printer whenever they log in to a different machine. 
 
So basically, what I am looking for is a method, script or application that allows the following:
 
-After profile (user) login, check either the computer-name of the thin-client or ip-address of thin-client (note that everybody connects to the same physical pc aka server, where the ubuntu desktop is running, so this needs to be a little sophisticated, as the script/app shouldn't retrieve the ip or computername of the server, but from the thin client connecting to the server);
-based on retreived name or ip-address, set a default printer from one of the installed printers available.
 
I have not tried to run the SetDefaultPrinter executable windows solution through something like Wine, I might do that but from what I understand, this will only set a default printer in the emulated windows environment Wine uses, not the Ubuntu environment. Does anybody have any suggestions?
 
Note: some background, I am currently contemplating about switching to linux altogether; I only need a maximum of ten machines for my employees, but the licensing fees MS is quoting to set up a Windows Server with Terminal capabilities is outrageous for a small company. I figured, if MS is not willing to deliver an affordable product for me, than I might as well embrace the power of open source and linux community help! I have some 5 years experience in linux, nothing hard-core though, but I can get around managing the environment, and doing some compiling.

---


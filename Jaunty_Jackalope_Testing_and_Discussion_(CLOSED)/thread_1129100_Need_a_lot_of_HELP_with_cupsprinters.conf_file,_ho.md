---
title: "Need a lot of HELP with cups/printers.conf file, how to fix?"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-04-18
Have an issue with network printing. I keep getting this error **tree connect failed (NT_STATUS_ACCESS_DENIED)**. I don't know why but out of nowhere this started. Somehow, it wants a password but none have been set. So, I read the printers.conf file after setting up the printer BUT before doing a print test.

sudo gedit /etc/cups/printers.conf

# Printer configuration file for CUPS v1.3.9 
# Written by cupsd on 2009-04-18 09:11 
<DefaultPrinter Canon-i950> 
Info Canon i950 
Location 
DeviceURI smb://192.168.0.4/i950 
State Idle 
StateTime 1240060296 
Accepting Yes 
Shared Yes 
JobSheets none none 
QuotaPeriod 0 
PageLimit 0 
KLimit 0 
OpPolicy default 
ErrorPolicy retry-job 
</Printer>

Looks good. Then trying to test print it reads; 


# Printer configuration file for CUPS v1.3.9 
# Written by cupsd on 2009-04-18 09:11 
<DefaultPrinter Canon-i950>
**AuthInfoRequired username,password**
Info Canon i950 
Location 
DeviceURI smb://192.168.0.4/i950 
State Idle 
StateTime 1240060296 
Accepting Yes 
Shared Yes 
JobSheets none none 
QuotaPeriod 0 
PageLimit 0 
KLimit 0 
OpPolicy default 
ErrorPolicy retry-job 
</Printer> 

I tried to delete **AuthInfoRequired username,password** but it simply rewrites the line.
How can this be fixed?
George

---

### Post by GARoss on 2009-04-19
bump

---

### Post by aasche on 2009-04-20
> **GARoss said:**
> 
I tried to delete **AuthInfoRequired username,password** but it simply rewrites the line.
How can this be fixed?

Why this should be fixed? If the printer is configured to use an username/password combination, this is required. Please post more infos about your network printer...

---

### Post by GARoss on 2009-04-20
> **aasche said:**
> Why this should be fixed? If the printer is configured to use an username/password combination, this is required. Please post more infos about your network printer...

Hello again, aasche!
Why, because it is a bug in the system that needs to be fixed!
[https://bugs.launchpad.net/bugs/305030](https://bugs.launchpad.net/bugs/305030)
[https://bugs.launchpad.net/bugs/283811](https://bugs.launchpad.net/bugs/283811)

---

### Post by GARoss on 2009-04-21
I thought I'd share this so anyone else doesn't spin there wheels as much as I have on this issue. This seems to be an issue in network printing where the PC that hosts the printer is running in Linux & another PC running Linux trying to print to that shared printer via the network fails with *tree connect failed (NT_STATUS_ACCESS_DENIED)* error. It prompts for passwords that cannot be set or satisfied. You can edit cupsd.conf file but it will not negate the password authorization prompt. And, the printer.conf file re-writes itself & cannot be edited, either. Oddly, when the host printer PC is running XP, the Linux PC can print via the network to the XP PC without issues.
This the response from launchpad;

"To answer your question (asked on bug #305030), no there is no news on this bug.
It would be written here if it were any.
You should expect this bug to be fixed in next version, Karmic Koala."

Some have had success with work-a-rounds; none worked for me. I posted at CUPS forum & they offered some help that didn't resolve it either. You can't win 'em all!;)
So, maybe in 9.10!

---


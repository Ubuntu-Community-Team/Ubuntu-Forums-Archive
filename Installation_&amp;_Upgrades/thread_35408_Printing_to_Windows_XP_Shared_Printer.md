---
title: "Printing to Windows XP Shared Printer"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by Ulixes on 2005-05-18
Have been tring for several weeks to get my Ubuntu systems to print to my shared printer on a Windows XP Pro machine.  Have samba set up and can manipualte files on XP machine through it.  I have tried everything in both of the HOWTOs, installed in Unix print drivers, changed printer location to every possible variation I can think of, turned off both machines firewalls and still nothing.  Just wondering if anyone knew of any obvious I am missing.  Any help will be greatly appreciated. 

System Info:  
Ubuntu 5.04 
Asus A7N8X Deluxe
3Com nic
Linksys router

Printer on Windows XP Pro
Lexmark X125 shared as LexmarkX

/etc/cups/printers.conf
[I]# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Wed May 18 19:52:18 2005
<DefaultPrinter X125>
Info X125
DeviceURI smb://Domain/ComputerName/lexmarkx
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>[/I]

---

### Post by Arthemys on 2005-05-18
What kind of error message are you getting if any?

Are you setting it up via gnome?

I'm able to print to my hp deskjet 3820 via cups / samba to my WinXP box just fine.

---

### Post by Ulixes on 2005-05-18
Connection failed with error NT_STATUS_ACCESS_DENIED.   

If i try to set it up with UNIX printer with the ip address of the XP machine it never gets passed look for server, just sits there.  And if in edit the /etc/cups.printer.conf file with user : password (with ip address or domian name/computer name) for the XP Machine it tells me its printing and doesn't give me an error, it seems as if it is but when I check the printer, nothing.

Trying to set this up in Gnome

---

### Post by Arthemys on 2005-05-19
Well if you're in GNOME...

Go to "System" "Administration" "Printing"

It's pretty straight forward at that point. Path of least resistance.

---

### Post by Ulixes on 2005-05-19
I have done that a couple thousand times, hence following the HOWTO, but since following them doesn't solve the problem I ask if anyone had any other advice.  :???:

---

### Post by Arthemys on 2005-05-19
Will the printer work if you install it locally?

Another thought was to check the security settings on the XP box for the printer and double check your user settings there.

Also, is this set up involving a domain at all?

---

### Post by Ulixes on 2005-05-19
I've checked everything.  I have tried to set it up with the domain name several ways and stills gives the same error.  If I try to give the IP address that the router gives the XP machine, it says its looking up location and does nothing.  Don't know what else to do.

---

### Post by tdi_veedub on 2005-05-19
Make sure that you have a guest account on the windows box connected to the printer.  It doesn't have to be enabled, it just has to be there.  Then, when you setup your printer in cups, make sure you provide "guest" as the user name.  The password can be nothing.

---

### Post by Ulixes on 2005-05-20
Tried with Guest account still nothing, but this time no error the printer icon pops up and say printing job 1 then closes.  But nothing happens at the printer. I ran sudo /usr/bin/smbclient -L location -U user and I can see the printer, so it is shared but either it gives me an access denied error or it does nothing.  

Something else happend this morning as well, last night a storm knock out the power for a couple hours, the XP machine was turned off.  This morning when I tried to set the printer up again I got the same error, went to check the XP machine again and it was still off.  So could there something wrong in samba not windows thats not allowing me to access the printer?

---

### Post by jrobcet on 2005-05-20
There was a person in this thread who had a problem similiar to yours: [http://ubuntuforums.org/showthread.php?t=32190](http://ubuntuforums.org/showthread.php?t=32190)

The solution was to disable "bidirectional support" on the XP machine. To disable it, go to printer properties on the XP machine (right click the printer and choose Properties). Click the Ports tab and uncheck "Enable bidirectional support".

I'm not sure if it will help in your situation, but it's worth a shot.

---

### Post by Ulixes on 2005-05-20
Thanks for the advice, but just talk to a friend that works for Lexmark and was told that the X125 is unsupported for linux.

---

### Post by Arthemys on 2005-05-20
[QUOTE=Ulixes]Thanks for the advice, but just talk to a friend that works for Lexmark and was told that the X125 is unsupported for linux.[/QUOTE]
That wouldn't explain the not authorized error you were getting though, the printer not being comptible would have garbled print outputs or just not print at all.

---

### Post by Ulixes on 2005-05-20
ya , but the printer is a combo, scan + fax + printer, something about they way windows authorizes use of the printer.  Don't know, said he had the same printer and could never get it working through XP over a network either.   :???:

---

### Post by Jellus on 2005-05-22
Hi,

Can you post .... all your configuration settings for samba ... users on linux machine ... and so on ... also post your settings on XP machine ... workgroup name .. users the works ...
trying to see some logic in your problem ... maybe we can help ... i.e. whoever cares enough to read your replies and feels like helping you out ... i think there are lots of people .. not just me being able to help you out .. perhaps ... don't include passwords though .... we don't need to know your passwords ... you just need to be consistent with the passwords on your network i think though ....

Greetings

Jellus

---

### Post by clb137 on 2005-05-22
[QUOTE=Ulixes]Have been tring for several weeks to get my Ubuntu systems to print to my shared printer on a Windows XP Pro machine.  Have samba set up and can manipualte files on XP machine through it.  I have tried everything in both of the HOWTOs, installed in Unix print drivers, changed printer location to every possible variation I can think of, turned off both machines firewalls and still nothing.  Just wondering if anyone knew of any obvious I am missing.  Any help will be greatly appreciated. 

System Info:  
Ubuntu 5.04 
Asus A7N8X Deluxe
3Com nic
Linksys router

Printer on Windows XP Pro
Lexmark X125 shared as LexmarkX

/etc/cups/printers.conf
[I]# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Wed May 18 19:52:18 2005
<DefaultPrinter X125>
Info X125
DeviceURI smb://Domain/ComputerName/lexmarkx
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>[/I][/QUOTE]

Hi there,

The simple way to get to print is edit the above file line
DeviceURI smb://Domain/ComputerName/lexmarkx

with 

DeviceURI smb://guest@Domain/ComputerName/lexmarkx

restart 


this will work
any probs give me a shout

cheers clinton

---

### Post by tom-ubuntu on 2005-05-22
Just fiddeled around with a XP Printer, finally solved it:

The Windowsmachine is using the "Guest" account for printing, no password. It seems to me, that the cups frontend is not writing it correctly to the configfile, atleast when you changed it once. 

I had to manually edit /etc/cups/printers.conf and change the path to
smb://guest:@Domain/ComputerName/sharedprinter

Dont know, if the ":" is necessary, but it is working for me.

Perhaps this helps someone.

Cheers Joe

---

### Post by Ulixes on 2005-05-22
Still nothing, the print dialog on Ubuntu acts like it sent a signal to the printer but the printers doesn't do anything.  The print properties doesn't give an error but nothing prints.

Just to the homepage for the X125 driver, the writer said that in order for the printer to work under linux it must to hooked directly to the linux machine, you can set it to allow windows machines to printer to it but you cannot print to a X125 that is installed on a Windows machine.

---


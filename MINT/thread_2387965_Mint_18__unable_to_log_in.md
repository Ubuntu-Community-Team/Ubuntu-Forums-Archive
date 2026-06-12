---
title: "Mint 18  unable to log in"
date: 2018-03-26
forum: MINT
---

### Post by roger--n on 2018-03-26
Hi  - Earlier today I actioned a system update - just the one item - but  did not note the name. as they came down regularly.   Now I cannot log  in.
When I try to Log in I get the error message that my session has lasted less than 10 seconds  

The xsession error log only has three lines in it

  syndaemon: no process found
/etc/mdm/Xsession: Beginning session setup... 
localuser:roger being added to access control list

  

I have been looking around the net for assistant - but all the  similar problems have many more lines of detail in the xsession error log  - It would seem  that the start up is just not running anything - any guidance for where  I can start looking for the problem would be gratefully accepted.   

 
 

Thanks 
Roger

---

### Post by deadflowr on 2018-03-26
*Thread moved to **MINT***

---

### Post by Karlchen on 2018-03-26
Hello, roger--n.

I assume that you are hit by a severe problem, which is caused by the software update of virtualbox-guest-* to version 5.1.34-dfsg-0ubuntu1.16.04.2.
The problem has been reported (and resolved) a dozen times only today in the [Linux Mint Forums]("https://forums.linuxmint.com/").
Linux Mint users of versions 18, 18.1 and 18.2 are frequently affected, because Mint installed virtualbox-guest-* by default, even in those cases where Mint was installed on bare metal and not in a VM at all.

Yet, as I mentioned above, the problem can be solved:

You boot up your Mint 18 till you see the graphical login dialogue. You cannot login to the graphical user interface.
Yet when you see the graphical login screen you can switch to one of the 6 pseudo console monitors by pressing <ctrl><alt><f1>.
Login to the console terminal.

Execute the command ```
 sudo apt-get purge virtualbox* 
```

Reboot and see whether login to graphical interface works again.

HTH,
Karl
--
Pointers to relevant threads:
[URL="https://forums.linuxmint.com/viewtopic.php?f=47&t=266431"]https://forums.linuxmint.com/viewtopic.php?f=90&t=266436#p1449036
[https://forums.linuxmint.com/viewtopic.php?f=47&t=266431](https://forums.linuxmint.com/viewtopic.php?f=47&t=266431)

[/URL]

---

### Post by roger--n on 2018-03-26
Brilliant  Thanks Karl - I will log out of this live CD version and go give it a try.

---

### Post by roger--n on 2018-03-26
Hi Karl.  I have done that .  On rebooting I get the message 
Welcome to emergency mode
After loggining in type journalctl -xb to view system logs systemctl reboot to reboot 
Systemctl  default to try again tobotinto default mode 
Give root password for maintenance or press control D to continue 
Pressing control  
Brings up the message 
[  40.896806] FAT-fs  (sda1) OK charred iso8859-1 not found 
And then the same welcome message

Any suggestions¿

---

### Post by roger--n on 2018-03-26
Just to say - Sda1 is the EFI system partition

---

### Post by roger--n on 2018-03-26
This machine is also loaded with windows 10 - So will try booting into that to see what it says about the EFI partition.

---

### Post by roger--n on 2018-03-26
I am making some progress - Windows 10 loads OK. So from that I presume the EFI partition is OK.  so the problem is with Linux.  I have logged on with an earlier version of the Kernel 4.4.0-21  and my mint has loaded ok.   So from that I presume there is a bug with the latest version 4.4.0-45.  Now my question is how do I resolve the problems with 4.4.0-45 
I have tried sudo apt-get install linux-generic  and sudo apt-get install --reinstall  all with out sucsess.  There are error messages about not being able to access ubuntu archives. 

Any suggestions?

---

### Post by roger--n on 2018-03-26
I am making some progress - Windows 10 loads OK. So from that I presume the EFI partition is OK.  so the problem is with Linux.  I have logged on with an earlier version of the Kernel 4.4.0-21  and my mint has loaded ok.   So from that I presume there is a bug with the latest version 4.4.0-45.  Now my question is how do I resolve the problems with 4.4.0-45 
I have tried sudo apt-get install linux-generic  and sudo apt-get install --reinstall  all with out sucsess.  There are error messages about not being able to access ubuntu archives. 

Any suggestions?

---

### Post by roger--n on 2018-03-27
Well - i have got rid of all my issues above by upgrading to Mint 18.3 - back on track

---

### Post by Karlchen on 2018-03-27
Hello, roger--n.

Glad to read that you have sorted out your issues. Sorry that you had to do so without more input from my side.
In the Linux Mint forum, I have not come across a case where the virtualbox-guest-* packages update triggered EFI boot problems as well.
Must be some special constellation on your system which triggered even more severe problems than those reported in the Linux Mint forum.

Best regards,
Karl

---


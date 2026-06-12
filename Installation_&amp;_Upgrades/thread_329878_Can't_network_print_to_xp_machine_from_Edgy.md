---
title: "Can't network print to xp machine from Edgy"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by Benchrest on 2007-01-02
I seem to have everything set up correctly fro all I've read here and elsewhere, but after document says its printing I get the message "paused: Job-hold-until-specified" I have no idea what that means. If someone could clarify that error message maybe it would be a clue. Nothing is sent to the xp machine. 

I had printing working with breezy, but unfortunately I failed to document my printer installation before installing Edgy. All I remember is the printer installation under breezy went very quick and easy. My XP machine is still set up as it was with breezy. Printer is shared and no guest user.

With edgy I have specified windows smb network printer, tried both name and ip address of xp machine. I am using the same printer, hp deskjet 5740. When I specify host, printer setup knows about my windows host and gives me its name as a choice. Same with the printer, it knows the printer share name on the xp machine and give me that choice. I have been working on this over a week. My edgy machine has access to the xp files through home network with samba. I am hopeful I am using the same smb.conf but I may have saved the wrong one. I can't remember that I installed samba before getting the printer to work with breezy anyhow. I made serious documentation errors and am paying for it.

---

### Post by Benchrest on 2007-01-02
I replaced my smb.conf with the example at the follwing thread by stormbringer  and it works!



[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by gaalderman on 2007-03-18
I had a similar problem in a similar situation (Edgy client trying to print to a printer on an XP box, jobs showing up as paused and marked 'job-hold-until-specified').  But my problem had a different solution.  Maybe this will help someone else out there.

Stormbringer's sample smb.conf in the link above didn't solve the problem for me.  What I found was a problem on the XP machine.  Apparently Norton Antivirus (which I run on the XP box) changes some settings in the Registry and that trashes XP sharing (both printer and file sharing).  I also couldn't access fileshares on that box.  If I tried to hit the XP box's shares from another Windows machine, I got the error message "Not enough server storage is available to process this command."  

See the following KB article for more info.  The fix is a simple change to a registry setting on the XP box.  It's worth a try if you're struggling with printing to an XP-shared printer from Ubuntu.

[http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078)

---

### Post by wpshooter on 2007-03-18
> **Benchrest said:**
> I replaced my smb.conf with the example at the follwing thread by stormbringer  and it works!



[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

That may or may not fix the problem but my contention is that sharing a printer from one computer to another should NOT be this difficult.  And yes, I call this difficult.  You should NOT have to edit files in order to get this to work.  All of this should be automated.

It is not this difficult under M/S windows, I know because I have done it numerous times.

Thanks.

---


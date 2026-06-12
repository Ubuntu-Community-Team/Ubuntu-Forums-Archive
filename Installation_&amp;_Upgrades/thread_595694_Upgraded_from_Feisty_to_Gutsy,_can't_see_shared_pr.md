---
title: "Upgraded from Feisty to Gutsy, can't see shared printer"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by ArielMT on 2007-10-29
Edit: Solution posted in second reply below.  Rest of original post follows:

A network upgrade on both systems broke network printing.

Before upgrading, both server and client were running Ubuntu 7.04, and printer sharing was a snap.  Server is a desktop, and client is a laptop I've made my main system, so it makes sense I'd want to print over a LAN instead of a cabled connection.

I have a Brother HL-2040 printer, and although installing it required some near-blind trust of Brother's installer scripts, I shared it effortlessly after confirming that printing locally works.  The printer showed up immediately on the client once telling it to show printers shared by other systems.

Both systems were upgraded to Ubuntu 7.10, and even though local printing on the server still works, the printer is no longer visible on the client.

I have tried every combination I can think of to publish and unpublish the printer, enable and disable sharing, and enable and disable using shared printers, on both the server and the client, and using both "Printer configuration" (system-config-printer) and the CUPS Web interface.

When using the Printer configuration program, I get the following message repeated five times in the CUPS error log:

[INDENT]E [29/Oct/2007:04:46:27 +0000] cupsdAuthorize: Local authentication certificate not found![/INDENT]

I don't get that error when using the CUPS Web interface.  But errors or no, I still can't see the printer published and shared by the server on the client.

---

### Post by ArielMT on 2007-10-29
Any advice at all on what to try next or retry would be most welcome.

---

### Post by ArielMT on 2007-10-29
Solved, although this should not have to be the solution.

I had to log in to the CUPS Web interface and hand-edit the [CUPS server configuration file]("https://localhost:631/admin?op=config-server").  I had to add the client IP address in the BrowseAddress directive as well as the three Allow directives in the Location sections. (Edit: The Allow directives were so I could resume troubleshooting the server from a Web browser on the client if necessary.)

Only after adding these lines and restarting CUPS on the server was the client finally able to see the printers again.  While I fully understand the security implications of not allowing any access off the system a printer's installed on by default, why must the on/off switch of sharing published printers on the LAN do nothing until this far less than intuitive step is taken?

I added the following on the server:

```
LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
**BrowseAddress 192.168.0.100**
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
**  Allow 192.168.0.100**
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
**  Allow 192.168.0.100**
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
**  Allow 192.168.0.100**
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
```

---

### Post by philhinz on 2007-10-31
The above almost exactly describes my problem.  I had a working printer in 7.04 that could be shared by other computers on the network.  After upgrading the computers to 7.10 I lost the printer sharing capability.  The above fix by ArielMT does NOT work for me.

Has anyone else seen this problem?  I can start hand-editing the CUPS file or looking into logs, but it used to "just work".

---

### Post by ArielMT on 2007-10-31
I think you'd want to substitute the IP address in the BrowseAddress option with your actual address.  I assume you've done that?

According to the [CUPS cupsd.conf help file (Browsing option)]("https://localhost:631/help/ref-cupsd-conf.html?TOPIC=References&QUERY=#Browsing"), it states that one or the other of BrowseAddress or BrowseProtocol must be specified in the cupsd.conf file on the server before its printers are visible on any clients.  It states that the default for BrowseProtocols (BrowseRemoteProtocols, specifically) is cups, but I don't believe that.  I admit I didn't find this before stumbling upon the workaround that worked for me.

I agree that the upgrade should not have broken this functionality, but the fact remains it did.

---

### Post by philhinz on 2007-10-31
Thanks for the pointer to the cups documentation.  According to it I want to put in the <server ip address>:631 for the Browser address. I added the following to my server cupsd.conf file and restarted cupsd and now I can see the printer on the client machine.

BrowseAddress 192.168.0.16:631

It still won't print from the remote machine, but this is progress . . .

---

### Post by LostAndFound on 2007-11-01
Hi,

I also have a shared printing problem after upgrading from Feisty to Gutsy.

My printer is connected to the Gutsy machine. In Feisty I was able to share the printer with a Feisty machine, a Mac, and a Windows machine all on a local network. After upgrading, printing only works from the Gutsy machine to which the printer is attached.

I noticed that cupsd.conf was overwirtten in the upgrade, so I first tried to share the printers again using the various Gnome and KDE dialogs. These did not work.

Next I restored cupsd.conf from a Feisty backup version. After this, the shared printer showed up on the other machine, but printing appears to be 'blocked'.

Would anyone know why the upgrade has stopped printer sharing from working? Is the format for the upgraded CUPS different?

Also, my CUPS password seems to have been changed

Any assistance greatly appreciated.

Lost.

---

### Post by Macchi on 2007-11-03
We are also experiencing problems with network shared printers on machines running Ubuntu Gutsy (clean installs). Shared printers are not shown despite attempting the most feasible combinations of settings. Everything worked OK on Feisty.

Have you seen any bug reports on shared printers and CUPS for Gutsy?

---

### Post by philhinz on 2007-11-05
I now have my printing working.  I played around with a bunch of access settings in the /etc/cups/cupsd.conf file to get things working but I think there are only two relevant bits.  

To see the server computer, as I said above, you put in

BrowseAddress 192.168.0.16:631

or whatever the ip address that your printer is attached to.  Then in cupsd.conf you need to allow "Enable Printer" which is in a Limit statement midway through the file.  I just commented out a Require statement and changed the order to "allow, deny" in this statement.  

Once this was done, I could go back to the configuration tool on my client machine (System>Admin>Printers) and enable the printer.  By looking in /var/log/cups/error_log I could tell that I had my Device URL set incorrectly (it wanted the server machine name, not its IP address).  Fixed this and it worked.

I hope fixing remote printing after the next upgrade is smoother :)

---

### Post by ArielMT on 2007-11-06
I'm noticing that on occasion, especially when the server starts up, CUPS has to be restarted on both the server and the client before the client will see the printer the server is sharing.  I don't need the server but for less than half a day on average, so I tend to leave it powered off quite a lot.  On the most recent occasion, a night and most of a day had passed between powering on the server and discovering that the printer was not seen from CUPS on the client.

Changing nothing and forcing CUPS to restart is the workaround, but something clearly broke between Feisty and Gutsy.

I haven't had the opportunity to look carefully for a bug report on either CUPS or Ubuntu.

---

### Post by ckoester on 2007-11-08
I can add a printer from a Windows XP machine, but the Printers and Faxes window only displays the printer as "opening".  Any attempt to open it or view the properties causes the Printers and Faxes window to freeze.

**Screenshot:**
[ATTACH]49549[/ATTACH]

---

### Post by vernhcclab on 2007-11-12
I also had problems with network printing when upgrading from Feisty to Gutsy.  This may not apply to any of your problems, but here are some things that I found.

The reason why I could not see the shared printers from the client machine was a problem with Firestarter.  If you have Firestarter on the server machine, it appears to block ipp.  I had to add a rule that allows the ipp service on port 631 (and I specified the IP address from my client machine).  In addition, (this was harder to track down), I needed to stop Firestarter on the client machine to see the shared printers.  This last one fooled me as I had done a simple test on two computers in my office at work and I could see the shared printers on the client without disabling Firestarter.  But, the client machine was a Feisty (7.04) machine (the server machine was running Gutsy).  This apparently makes a difference, as installing Gutsy on the client machine with Firestarter enabled won't let me see the shared printers.

With Firestarter (on Gutsy) disabled on the client machine, I could right-click on the now visible shared printers and look at the connection.  The connection string now includes the port number.
Feisty server:  ipp://<ip>/printers/PrinterName
Gutsy server:  ipp://<ip>:631/printers/PrinterName

If I install gnome-cups-manager (sudo apt-get install gnome-cups-manager; the older printing manager) I can add a new printer with the settings that I see with Firestarter disabled.  Then, I enable Firestarter again and use the new printer that I manually added.  This seems to work okay so far.

I also found that starting up Synaptic and searching on cupsys, and then reinstalling everything associated with cupsys (including libcupsys2), seemed to help after I had messed up the configuration files.

---

### Post by ArielMT on 2007-11-29
The problem I have now is that, whenever the server is restarted and once a day whether the server ran overnight or not, cups has to be restarted on the server before the printer becomes visible on the client.  The reason is still not known.

Especially troubling is the still unknown reason why cups needs to be restarted immediately after start-up.  I gave it up to four hours after start-up to show the printer, and it never did; yet after restarting cups, the printer was visible within a minute.

I removed firestarter in favor of direct ip-tables control a few weeks ago, and that resolved my port access issues.

---

### Post by ArielMT on 2008-01-05
My problem fixed itself, and I don't know when or why.

---

### Post by ArielMT on 2008-01-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/177075](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/177075) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				For those of you still having network printing problems since upgrading to Gutsy, check this out.  A bugfix was pushed out through software updates last night.

[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/177075](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/177075)

The bug [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/173470](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/173470) appears to be related.

---


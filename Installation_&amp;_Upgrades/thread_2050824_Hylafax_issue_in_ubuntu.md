---
title: "Hylafax issue in ubuntu"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by chackorojith on 2012-08-31
Hi,

This is on setting up Hylafax in Ubuntu server.We are installing Hylafax in Ubuntu server 12.04. We use apt-get install to install the hylafax server and client.
 
   Everything goes well. Our US Robotics FAX modem is detected by the installation ( it says Class 1 modem). We are trying to send fax through YajHFC ( the java client running in another machine). Looks like the server receives the FAX send request.

  Unfortunately sudo faxstat -s give :

 Modem ttyACM0 : Waiting for modem to come ready.

  What could be the problem.?  Ours is a telephone line.
Could it be that this works only with FAX lines ..?

Or this is some software issue ?
 
Rojit

---

### Post by SeijiSensei on 2012-08-31
Is it a dedicated phone line or an extension off a central switch?  Sometimes modems and switches do not coexist well.  If you are using a telephone switch, you might ask your vendor.

---

### Post by chackorojith on 2012-09-04
Hi,

Thanks for responding.
Yes, this is a dedicated phone line.
No switches or extensions involved.
Meanwhile is there any Hylafax logs or traces that we can verify..?
*

Rojit

---

### Post by SeijiSensei on 2012-09-04
It's been quite a few years since I used hylafax.  Do you see logs in /var/log?  Is there a log directory specified in the configuration files?

I'm in the US, and here fax modems work just fine with "plain-old-telephone-service" or POTS lines. However I don't think they work with digital services like ISDN, though I could easily be wrong about that.  Have you asked your telephone provider?  

If you have a laptop around with a built-in modem, try connecting that to the line and see if you can send a fax.  It's pretty easy to do from Windows as I recall.  I don't suppose you have an actual fax machine or an all-in-one device that you could use for testing?  I'd focus on troubleshooting the connection first.  If that doesn't work, then you'll know not to waste time on hylafax.  If you can send a fax with a different device, though, then you'll know it has something to do with the hylafax configuration.

Now I just have a cheap online fax service from [extremefax.com]("http://www.extremefax.com/"). I've got a few old Courier modems around, too.  I remember paying $300 for one of those back in the day, but they were rock solid.

---


---
title: "Please confirm these Nautilus Bugs/Enhancements"
date: 2008-08-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MaX on 2008-08-16
These are in Gnome's Bugzilla and not in launchpad because they are not Ubuntu specific. But they still need help with confirming bugs.
**Nautilus**
[LIST]
[*][Scrolling doesn't work in Compact View #537552]("https://bugzilla.gnome.org/show_bug.cgi?id=537552")
[*][Show total file size in Status bar #504771]("https://bugzilla.gnome.org/show_bug.cgi?id=504771")
[*][Right click menu for trash is to crowded #548072]("https://bugzilla.gnome.org/show_bug.cgi?id=548072")
[/LIST]
**GTK+**
[LIST]
[*][selection lists need scrolling #344220]("https://bugzilla.gnome.org/show_bug.cgi?id=344220")
[/LIST]

If you like my suggestions please add constructive criticism or suggestions in the comments.

Feel free to list more bugs that need confirming.

---

### Post by MaX on 2008-08-17
Please take time to either confirm these bugs or if you are unable to reproduce them, comment about that too. Since knowing if a bug is real or not is a problem for the developers. All these are crashes so they should be easy to notice.
**Unconfirmed Critical bugs**
[LIST]
[*][crash in Home Folder: I've uninstalled nautilu...]("https://bugzilla.gnome.org/show_bug.cgi?id=506435")
[*][crash in nautilus_icon_factory_get_type () at nautilus-ic...]("https://bugzilla.gnome.org/show_bug.cgi?id=509527") 
[*][crash in set_pending_icon_to_reveal() in nautilus-icon-co... ]("https://bugzilla.gnome.org/show_bug.cgi?id=527575")
[*][crash in Open Folder: tried to open the proper... ]("https://bugzilla.gnome.org/show_bug.cgi?id=534093")
[*][crash in Home Folder: drag and drop. icon move... ]("https://bugzilla.gnome.org/show_bug.cgi?id=536904")
[*][crash in File Browser: I was opening a samba sh... ]("https://bugzilla.gnome.org/show_bug.cgi?id=544674")
[*][crash in File Browser: ]("https://bugzilla.gnome.org/show_bug.cgi?id=545224")
[*][crash in Open Folder: Trying to open a folder ... ]("https://bugzilla.gnome.org/show_bug.cgi?id=546889")
[*][crash in Open Folder: Attempting to rename a f... ]("https://bugzilla.gnome.org/show_bug.cgi?id=546965")
[*][crash in Open Folder: Changing Controls under ... ]("https://bugzilla.gnome.org/show_bug.cgi?id=547681")
[*][crash in Open Folder: I had just opened the fo... ]("https://bugzilla.gnome.org/show_bug.cgi?id=547817")
[*][crash in File Browser: mirando propiedades de d... ]("https://bugzilla.gnome.org/show_bug.cgi?id=547834")
[*][crash in Open Folder: I wasn't even looking at... ]("https://bugzilla.gnome.org/show_bug.cgi?id=547947")
[*][crash in Open Folder: wanna open an ifo-file (... ]("https://bugzilla.gnome.org/show_bug.cgi?id=548001")
[*][crash in File Browser: Grabando archivos en el ... ]("https://bugzilla.gnome.org/show_bug.cgi?id=548099")
[*][crash in Home Folder: Backuping files ]("https://bugzilla.gnome.org/show_bug.cgi?id=548106")
[*][crash in Open Folder: Nautilus regular reboot.... ]("https://bugzilla.gnome.org/show_bug.cgi?id=548112")
[*][crash in Open Folder: Just another gnome/nauti... ]("https://bugzilla.gnome.org/show_bug.cgi?id=548113")
[*][crash in Open Folder: Log on into system from ... ]("https://bugzilla.gnome.org/show_bug.cgi?id=548123")
[*][crash in Computer: ]("https://bugzilla.gnome.org/show_bug.cgi?id=548127")
[*][crash in Home Folder: After having yesterday u... ]("https://bugzilla.gnome.org/show_bug.cgi?id=548147")
[*][crash in Open Folder: loading a large director...]("https://bugzilla.gnome.org/show_bug.cgi?id=548172")
[/LIST]

---

### Post by cariboo on 2008-08-17
I think you better check your links, as I get a page load error on all of them.

Jim

---

### Post by plun on 2008-08-18
OT but maybe important, bugzilla.gnomes security certificate seems to be broken for Firefox 3

> 
**_Add Security Exception_**

   1.  Click the **Add Exception**&#8230; button.

   2. In the Add Security Exception dialog, click the **Get Certificate** button.

   3. Once the certificate has been retrieved, you can optionally view it by clicking the View button.

   4. Click Confirm Security Exception (the Permanently Store This Exception checkbox is enabled by default).


Nautilus bugs are nevertheless a difficult area ... a challenge.

---

### Post by Nullack on 2008-08-18
Its a self signed certificate

---

### Post by napsy on 2008-08-18
While we're at it. Please confirm bug [http://bugzilla.gnome.org/show_bug.cgi?id=548234](http://bugzilla.gnome.org/show_bug.cgi?id=548234)

It's not critical but very annoying.

---

### Post by MaX on 2008-08-18
Napsy: You know you have gotten an answer right?

---

### Post by Nullack on 2008-08-18
Max I know I thanked you in your post, but I just want to quickly put some words down to say why and encourage other people to get into this sort of upstream stuff. It saves us time, and heres why:

* Most of the code from upstream is the same as whats in Ubuntu
* The upstream bug lists may already have the bugs were grappling with to understand and overcome in Ubuntu
* it helps get action on the bugs when it is upstream and not a debian/ubuntu issue

For example I did a bug report on gnome's bugzilla about not being able to set the maximum transmission unit in my ethernet nic and one of the devs has identified the problem. Plus his fix will also fix how NM is ignoring static setups for my nic as well.

Looking into upstream really does get results.

---

### Post by MaX on 2008-08-18
Thanks Nullack.

Trouble right now is many people HERE in the Development forums use up more time bickering about how ugly the theme is and re-creating the same threads from the last release over and over again.
There are more important issues than the theme.

---

### Post by philinux on 2008-08-18
Links **Crash In** fail with this error.

Secure Connection Failed

bugzilla.gnome.org uses an invalid security certificate.

The certificate is not trusted because the issuer certificate is not trusted.

(Error code: sec_error_untrusted_issuer)

    * This could be a problem with the server's configuration, or it could be someone trying to impersonate the server.


    * If you have connected to this server successfully in the past, the error may be temporary, and you can try again later.

---

### Post by MaX on 2008-08-19
It's because they are HTTP**S** remove the S and they will work.
Or add an exception

---

### Post by Nullack on 2008-08-19
> **philinux said:**
> Links **Crash In** fail with this error.

Secure Connection Failed

bugzilla.gnome.org uses an invalid security certificate.

The certificate is not trusted because the issuer certificate is not trusted.

(Error code: sec_error_untrusted_issuer)

    * This could be a problem with the server's configuration, or it could be someone trying to impersonate the server.


    * If you have connected to this server successfully in the past, the error may be temporary, and you can try again later.

Its a self signed certificate :)

---

### Post by plun on 2008-08-19
> **MaX said:**
> These are in Gnome's Bugzilla and not in launchpad because they are not Ubuntu specific. But they still need help with confirming bugs.

If you like my suggestions please add constructive criticism or suggestions in the comments.

Feel free to list more bugs that need confirming.

Well, version 2.23.90 (beta) is rolled out and its difficult with "unstable" conditions to check bugs

I filed a new one to the list

**Nautilus crashes when viewing mounted archieves, iso-files**
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259304](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259304)

Edit, new bug
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259343](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259343)

---

### Post by tawmas on 2008-08-19
Just confirmed **Show total file size in Status bar #504771**, would be very nice to have it!

Though I guess it's not really high-priority... :-|

---

### Post by Nullack on 2008-08-19
That would be nice but I dont think it will happen this gnome cycle as its passed the feature freeze point of the schedule:

[http://live.gnome.org/TwoPointTwentythree](http://live.gnome.org/TwoPointTwentythree)

---

### Post by Alistair George on 2008-08-19
Nautilus is letting networking down too see these urls:
[http://ubuntuforums.org/showthread.php?t=894892&highlight=nautilus](http://ubuntuforums.org/showthread.php?t=894892&highlight=nautilus)
[http://ubuntuforums.org/showthread.php?t=830032&highlight=couldn%27t+display+network%3A%2F%2F%2F&page=2](http://ubuntuforums.org/showthread.php?t=830032&highlight=couldn%27t+display+network%3A%2F%2F%2F&page=2)

Cheers,
Alistair.

---

### Post by plun on 2008-09-01
New versions

Nautilus
[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006188.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006188.html)

Eel
[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006187.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006187.html)

So its probably last chance for more complicated bug hunts...

---

### Post by plun on 2008-09-03
Since today, (yesterdays updates) Nautilus is crashing frequently for me.

Anyone else ?

Reinstalled both Nautilus and Eel without any luck.


PCMans file manager works....:)

---


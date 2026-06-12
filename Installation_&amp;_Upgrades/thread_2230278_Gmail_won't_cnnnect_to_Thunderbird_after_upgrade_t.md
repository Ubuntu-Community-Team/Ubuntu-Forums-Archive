---
title: "Gmail won't cnnnect to Thunderbird after upgrade to 14.04"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by CosmicTigger on 2014-06-18
Hi everyone

I've recently upgraded to Trusty from Saucy, after using the previous releases for about five years on and off. In the previous release, I was able to configure my five Gmail addresses to work via Thunderbird without any problems. Since 14.04 came out, however, it doesn't seem to connect at all.

I've double-checked my IMAP settings in Gmail itself, and they're all set to 'enable.' I've changed the server settings from 'googlemail' to 'gmail', but to no avail. A friend of mine has had the same problem, so we're stuck with using the Gmail app - which is a pain when you're trying to switch from one to the other quickly.

Does anyone have any ideas how I can work around this? As an experiment this afternoon I tried connecting via Evolution, but that was a no-go as well.

Thanks in advance :)

---

### Post by gifford on 2014-06-18
The server settings imap.googlemail.com
Outgoing is smtp.googlemail.com

I have never had any trouble using gmail with multiple accounts in Thunderbird and am using 14.04.

---

### Post by CosmicTigger on 2014-06-18
Hi Gifford, thanks for posting.

 I've tried both 'googlemail' and 'gmail' in the server settings, but no joy. I've double-checked the port settings, and even reset my passwords in case they were causing the problem. I've turned the clock back to 13.04 now, and Thunderbird worked first time. 

I must be missing something obvious, but I'm blowed if I can see what.

---

### Post by Kathy_Pratt on 2014-08-25
i just installed Ubuntu and i keep getting an Error "unable to locate mail spool file" does anyone know what this is asking for?

---

### Post by BazBear on 2014-08-25
I gave up on T-bird. I had used it for years on Windows, and then Lubuntu for a few more. After an update last winter (northern hemisphere) I simply could not make it save certain settings. I set it to suck the new e-mails off of Gmail, and delete them from the server, no foxtrotting way (tried several proposed fixes).

---

### Post by pfeiffep on 2014-08-25
> **Kathy_Pratt said:**
> i just installed Ubuntu and i keep getting an Error "unable to locate mail spool file" does anyone know what this is asking for?

I've not had that problem but I did find a [solution]("http://askubuntu.com/questions/328143/thunderbird-showing-unable-to-locate-mail-spool-file-on-installing-gmail-accou")> [COLOR=#333333][FONT=UbuntuRegular]Just go to the file browser and type CTRL+H to reveal hidden files, then delete the .thunderbird folder.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]After that, thunderbird should open fine.[/FONT][/COLOR]


---


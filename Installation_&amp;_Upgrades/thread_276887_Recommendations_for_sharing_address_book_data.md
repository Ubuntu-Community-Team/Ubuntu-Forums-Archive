---
title: "Recommendations for sharing address book data"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by driggins on 2006-10-13
Greetings,

I need a solution for sharing contact data (address book) amongst my small office. I am a refugee of MS Exchange and newbie to Ubuntu.

I notice vtiger and sugarCRM, but both solutions are way overkill for our needs.

My client computers are Win XP. It would be convenient if we could access this shared address book via MS Outlook - this is not a deal killer, however.

Secondarily, I have a bunch of contact data in MS Access format that I would want to upload to whichever solution fits the best.

This data/app would reside on Ubuntu Server 6.06.

Thoughts?
daryl

---

### Post by jose3 on 2006-10-13
I see a posible solution.
You could setup LDAP on your Ubuntu server. LDAP is like a directory server that lets you define -among other things- adresses that can be consulted by the mail clients in the terminals (linux-windows is the same) with thunderbird or Outlook. This is like a port opened for a service where the mail program asks for addresses while starting FE.

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)




Regards.

---


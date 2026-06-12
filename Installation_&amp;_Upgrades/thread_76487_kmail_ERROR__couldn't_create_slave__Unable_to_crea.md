---
title: "kmail: ERROR: : couldn't create slave : Unable to create io-slave"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by somez on 2005-10-15
I've just upgraded to Kubuntu 5.10 breezy, and I get somekind of strange errors with kmail.

I've found a topic for my problem, where the guy describes he's problem lik this:

- When downloading mail

Pop window saying:

'Could not start process pop3.'

and shell says:

kmail: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Error loading 'kio_pop3'.

- When sending messages

Shell says:

kmail: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Error loading 'kio_smtp'. 

I have the same problem, and don't know what to do.

---

### Post by somez on 2005-10-15
Guys I really need your help, because this problem affects the whole KDE and I really need kontact.

---

### Post by ryanschiffbauer on 2005-10-30
I had the same problem.  Just run:

sudo apt-get install kdebase

And voila, your problems are solved!  :)

It needs that file dependency for some reason.

Ryan

---

### Post by made_in_heaven on 2007-11-13
ryanschiffbauer, you really great!! :)
i was really despaired, i disposed myself to reinstall all system, but have found your message intime.
 I have Slackware, so by analogy i did:
instalpkg kdebase-3.3.2-i486-1.tgz
and this faken error has disappeared!
Add, i have recieved this error after installing new version of qt .

---

### Post by Tari Narmolanya on 2008-01-23
darn, I have a similar problem, but i am using gnome. Does it take any effect to Ubuntu/gnome environment ?? To make it simple, i just do not want to have the Kubuntu Splash on startup .... :s

Oh just FYI: kdebase-bin and kdebase-data are installed, but not kdebase ...

---


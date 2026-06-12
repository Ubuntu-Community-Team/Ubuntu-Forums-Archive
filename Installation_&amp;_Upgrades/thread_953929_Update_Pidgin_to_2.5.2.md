---
title: "Update Pidgin to 2.5.2"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by mamous on 2008-10-20
Hi i know that I'm new on this forum and this is my first post so..
I would like to tell how to update pidgin 2.4.1 to 2.5.2
**[COLOR="Red"]1-[/COLOR]** u have to download these three files
          1- pidgin ([http://www.getdeb.net/download/3289/0]("http://www.getdeb.net/download/3289/0"))  (559.9 kB)
          2- pidgin-data ([http://www.getdeb.net/download/3289/1]("http://www.getdeb.net/download/3289/1")) (6.8 MB)
          3- Libpurple0 ([http://www.getdeb.net/download/3289/2]("http://www.getdeb.net/download/3289/2")) (1.5 MB)
**[COLOR="Red"]2-[/COLOR]** Go to the Synaptic package manager and search for pidgin.
Mark "Pidgin" and "pidgin-data" for removal, it will advise its removing a libpurple0 file as well.
**[COLOR="Red"]3-[/COLOR]** Install the pidgin-data file first (right click and open with the GDebi package installer)
Once pidgin-data is installed then right click on the new libpurple0 installer and install that, then do the same for pidgin.
**[COLOR="Red"]4-[/COLOR]** Start pidgin and it should be working fine.

---

### Post by Occam on 2008-10-21
Awesome - worked like a charm. Thank you!

:popcorn:

---

### Post by mamous on 2008-10-21
You are welcome...

And here is the Version Changes of Pidgin

   **[COLOR="Red"]libpurple:[/COLOR]**
     * Fixed a crash on removing a custom buddy icon on a buddy.
     * Fixed a crash caused by certain self-signed SSL certificates.
     * Enable a number of strong ciphers which were previously disabled
       when using NSS.  (Thanks to Marcus Trautwig.)
 .
   **[COLOR="Red"]Pidgin:[/COLOR]**
     * The status selector now saves your message when changing status.
     * Fix a case where a conversation window could close unexpectedly.
     * A mute sounds option has been added to the preferences window to
       help with discoverability.  CTRL+S is no longer bound to mute.
     * Added ability to change the color of visited links (using the theme
       control plugin, or setting the color in ~/.gtkrc-2.0)
     * Fix a crash occuring when a custom smiley is deleted and re-added and
       used in an open conversation after being re-added.
 .
   **[COLOR="Red"]Finch:[/COLOR]**
     * A new 'Nested Grouping' option in the 'Grouping' plugin. Group
       hierarchies are defined by the '/' character in the group names.
     * A bug was fixed where some key-bindings wouldn't work with some TERMs
       (e.g. xterm-color, screen-linux etc.)
 .
   **[COLOR="Red"]MSN:[/COLOR]**
     * Operations (such as moving to a new group) on contacts that were added
       in the same session should now complete correctly, and not cause
       synchronization errors at next login.
     * Minor fixes to login process during a server transfer.
     * Restored the "Has You" feature to the MSN protocol tooltips.
     * ADL 205/214/etc errors should no longer prevent login.
 .
   **[COLOR="Red"]XMPP:[/COLOR]**
     * Sending and receiving custom smileys using the specification in
       XEP-0231 (bits of binary) and XHTML-IM
 .
   **[COLOR="Red"]Yahoo:[/COLOR]**
     * Only send a Ping once every hour.  This prevents the account from
       being disconnected from the server periodically.

---

### Post by bbc on 2008-10-22
Worked fine. You rule. Thank you.

---

### Post by zvacet on 2008-10-22
Why don´t just add getdeb to your source list?

```
gksudo gedit /etc/apt/sources.list
```

```
deb http://ubuntu.org.ua/ getdeb/
```

save file and exit.

```
sudo apt-get update
```

---

### Post by mamous on 2008-10-23
Thank you for advice

But I'd like to do on my own Because it is good to teach me how to do thing my own if i hade any Trouble

---

### Post by muks on 2008-10-27
Thanks Mamous..
I was looking for a method which'll update my pidgin without any problems. Yours was superb.

---

### Post by mamous on 2008-11-10
Thanks All i'm happy that i help you...
And I wish that was good becouse it is the first time for me to join [COLOR="Red"]**_Ubuntu Forums_**[/COLOR]...
And you all welcome .

---

### Post by juank8041 on 2008-11-18
Works great but, if you are installing on Ubuntu 8.04 amd64 remember to download the appropriate packages:

* pidgin_2.5.2-1~getdeb1_amd64.deb from [http://www.getdeb.net/download/3290/0]("http://www.getdeb.net/download/3290/0") (617.7 kB)
* pidgin-data_2.5.2-1~getdeb1_all.deb from [http://www.getdeb.net/download/3290/1]("http://www.getdeb.net/download/3290/1") (6.8 MB)
* libpurple0_2.5.2-1~getdeb1_amd64.deb from [http://www.getdeb.net/download/3290/2]("http://www.getdeb.net/download/3290/2") (1.7 MB)

Also, when installing libpurple0, I was asked to install libsilc-1.1-2. I did this through Synaptic Package Manager.

Thanks,

Juan

---

### Post by vegetarianshrimp on 2008-11-30
For some reason, the libpurple0 and the pidgin don't work. I get a error message saying it's the wrong architecture. Well, on the bright side, you inspired me to use the Synaptic Package Manager, and now I have 30 plugins for Pidgin that I don't even use!;)

---


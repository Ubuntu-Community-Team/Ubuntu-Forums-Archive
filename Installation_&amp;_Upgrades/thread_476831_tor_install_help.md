---
title: "tor install help"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by w00taliter on 2007-06-17
ok i followed these instructions
"
1. Run the command: sudo apt-get install tor privoxy
2. Run the command: sudo gedit /etc/privoxy/config
3. Add the line (including the period at the end): forward-socks4a / localhost:9050 .
4. Comment out the line: logfile logfile
5. Comment out the line: jarfile jarfile
6. Restart the Privoxy service: sudo /etc/init.d/privoxy restart
" 
i installed torbutton and i also am confused about what it means by comment out of the line logfile logfile  same with the jarfile jarfile but here is what i am really confused about i thought i did it right but i guess i did not do it right because on whatsmyip.com my ip is not changeing once its dissabled please tell me what i did wrong


oh and also is the config file supposed to be set up like this 


#  The "hide-console" option is specific to the MS-Win console version
#  of Privoxy.  If this option is used, Privoxy will disconnect from
#  and hide the command console.
#
#hide-console

#“logfile logfile”forward-socks4a / localhost:9050 .

---

### Post by Pugwash on 2007-06-27
> **w00taliter said:**
> ok i followed these instructions
"
1. Run the command: sudo apt-get install tor privoxy
2. Run the command: sudo gedit /etc/privoxy/config
3. Add the line (including the period at the end): forward-socks4a / localhost:9050 .
4. Comment out the line: logfile logfile
5. Comment out the line: jarfile jarfile
6. Restart the Privoxy service: sudo /etc/init.d/privoxy restart
" 
i installed torbutton and i also am confused about what it means by comment out of the line logfile logfile  same with the jarfile jarfile but here is what i am really confused about i thought i did it right but i guess i did not do it right because on whatsmyip.com my ip is not changeing once its dissabled please tell me what i did wrong


oh and also is the config file supposed to be set up like this 


#  The "hide-console" option is specific to the MS-Win console version
#  of Privoxy.  If this option is used, Privoxy will disconnect from
#  and hide the command console.
#
#hide-console

#&#8220;logfile logfile&#8221;forward-socks4a / localhost:9050 .

No, its supposed to be like this:

```
#  The "hide-console" option is specific to the MS-Win console version
#  of Privoxy.  If this option is used, Privoxy will disconnect from
#  and hide the command console.
#
#hide-console
#

forward-socks4a / localhost:9050 . 
```

and put a "#" in front of the "logfile logfile" and "jarfile jarfile" lines (search for them using "ctrl +f" in the file). That's what it means by comment out.

---

### Post by fyrefly07 on 2007-07-13
I can not seem to get TOR to run after installing.  I've tried installing using apt-get  ie:

sudo apt-get install tor

and also by downloading and compiling the source from tor.eff.org.

After either attempt at install I get:

```

~$ tor
Jul 13 00:12:16.032 [notice] Tor v0.1.1.26. This is experimental software. Do not rely on it for strong anonymity.
Jul 13 00:12:16.033 [notice] Initialized libevent version 1.1a using method epoll. Good.
Jul 13 00:12:16.035 [warn] /var/lib/tor is not owned by this user (shaun, 1000) but by debian-tor (110). Perhaps you are running Tor as the wrong user?
Jul 13 00:12:16.035 [warn] Failed to parse/validate config: Couldn't access/create private data directory "/var/lib/tor"
Jul 13 00:12:16.035 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
~$ 

```

Is this permissions error a result of a bad install??

---

### Post by fyrefly07 on 2007-07-15
Alright...   nevermind.  Torbutton in firefox seems to be working fine.  Didn't realize that I wasn't supposed to be starting tor from the CLI.

---


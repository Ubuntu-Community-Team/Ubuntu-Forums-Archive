---
title: "PPPoE always on"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by alexj on 2005-04-23
Hi Guys,

I set PPPoE using pppoeconfig. It works fine, however two more steps are needed:
 - I need to make sure the link goes up on boot;
 - I need to make it to restore connection if it goes down;

Any advice will be appreciated

Cheers,

Alex

---

### Post by RonP on 2007-09-06
i think this would be nice. My PPPOE is nothing less then trouble.

---

### Post by zvacet on 2007-09-06
To restore it 

```
pon dsl-provider
```

---

### Post by kmashraf on 2008-04-12
Just to add my experience in setting up a on demand pppoe connection in Linux Mint 4.0 Daryna. Essentially Ubuntu but a variant.
The dsl connection works as a on demand connection in Windows XP (dual boot) using a username and password.
I ran 'sudo ppoeconfig' (without the quotes) in a terminal.
I was led thru' the menus where I chose all the default options.
gave the username and password (displays as plain text)
Chose to start the connection at boot.
But at first when I tried the connection with 'pon dsl-provider' (without rebooting) and then checking with the 'plog' command found that the connection was refused (access denied) at the provider end due to PAP authentication error.
I repeated the pppoeconfig setup a no. of times but kept getting the same error.
Then when I was going thru one of the setups I noticed that 'username' was appended to the actual username. I removed the above append and doing so seems to have fixed the PAP authentication error.
Subsequently it connected to the dsl service without any trouble whatsoever with the command 'pon dsl-provider' disconnected with 'poff' command and I could monitor all this with the 'plog' command.
Also since I had chosen to have the connection started on boot it was up and ready when booted up.
It would be great if a frontend for this can be written up.

---


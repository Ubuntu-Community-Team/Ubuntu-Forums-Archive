---
title: "vvin switches off my machine"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by edemark on 2005-08-08
Hi all
I have a problem with vvin emulation as it switches off my laptop. I suffer from this problem when i use the following: qemu with vvin or when i use cedega. The truth is that i have nothing in hand. I do not know how to find out the origin of this problem.
I dont know if someone has this same problem. So please help. So far I can only suppose that this is a heat issue but i am only guessing. Notwithstanding i suppose that this issue is related with ubuntu as i was playing happily in suse. Now the same game Homeworld swithches off my computer. 

Any idea what to look for to find resolution to this issue?

pls help i do not want to get back to dual boot 

problem ocurred:
playing homewolrd, installing Armed and Dangerous, and in runing qemu with 98

thanks in andvance

---

### Post by edemark on 2005-08-09
[QUOTE=edemark]Hi all
I have a problem with vvin emulation as it switches off my laptop. I suffer from this problem when i use the following: qemu with vvin or when i use cedega. The truth is that i have nothing in hand. I do not know how to find out the origin of this problem.
I dont know if someone has this same problem. So please help. So far I can only suppose that this is a heat issue but i am only guessing. Notwithstanding i suppose that this issue is related with ubuntu as i was playing happily in suse. Now the same game Homeworld swithches off my computer. 

Any idea what to look for to find resolution to this issue?

pls help i do not want to get back to dual boot 

problem ocurred:
playing homewolrd, installing Armed and Dangerous, and in runing qemu with 98

thanks in andvance[/QUOTE]
 Hi all I am still on this issue and it is a bit desperate please if you have any idea help I do not even know where to start 
once again games in cedega a vvin in qemu switches off my machine 
I have not experienced this before (using suse) though i was not using qemu 

so please what to look for 
log?

please help
please
and thanks

---

### Post by edemark on 2005-08-09
[QUOTE=edemark]Hi all I am still on this issue and it is a bit desperate please if you have any idea help I do not even know where to start 
once again games in cedega a vvin in qemu switches off my machine 
I have not experienced this before (using suse) though i was not using qemu 

so please what to look for 
log?

please help
please
and thanks[/QUOTE]
 so it has happened again i was installing a game on cedega when the machine went off. I post here my /var/log/messages:
Aug  9 17:13:12 localhost gconfd (intento-11936): starting (version 2.10.0), pid 11936 user 'intento'
Aug  9 17:13:12 localhost gconfd (intento-11936): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  9 17:13:12 localhost gconfd (intento-11936): Resolved address "xml:readwrite:/home/intento/.gconf" to a writable configuration source at position 1
Aug  9 17:13:12 localhost gconfd (intento-11936): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  9 17:14:43 localhost kernel: UDF-fs: No VRS found
Aug  9 17:36:26 localhost -- MARK --
Aug  9 17:58:27 localhost syslogd 1.4.1#16ubuntu6: restart.

I just can not find anything 
pls help if you have any idea

thanks in advance

---

### Post by edemark on 2005-08-10
[QUOTE=edemark]so it has happened again i was installing a game on cedega when the machine went off. I post here my /var/log/messages:
Aug  9 17:13:12 localhost gconfd (intento-11936): starting (version 2.10.0), pid 11936 user 'intento'
Aug  9 17:13:12 localhost gconfd (intento-11936): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  9 17:13:12 localhost gconfd (intento-11936): Resolved address "xml:readwrite:/home/intento/.gconf" to a writable configuration source at position 1
Aug  9 17:13:12 localhost gconfd (intento-11936): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  9 17:14:43 localhost kernel: UDF-fs: No VRS found
Aug  9 17:36:26 localhost -- MARK --
Aug  9 17:58:27 localhost syslogd 1.4.1#16ubuntu6: restart.

I just can not find anything 
pls help if you have any idea

thanks in advance[/QUOTE]
 So it seems to me that my problem is really not a common one (i just guessing as there is no answer) anyway i keep on as i would love to get rid of this switch off
One of the things i really liked in linux that it was not necesary to switch it off, however since i use ubuntu i feel somehow a bit vvin-ish restarting my laptop every time i play or install games (yes it is true just with vvin games and not with linux games)

So if you have any idea than pls write 

I could welcom if someone would tell me where to start to look
I have no idea

pls pls HELP
thanks

---


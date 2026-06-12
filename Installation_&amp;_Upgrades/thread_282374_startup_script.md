---
title: "startup script"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2006-10-22
Heya
I have some lines in /etc/rc.local

ifconfig...
route add...
./home/dmsn/firewall start
exit 0


Why it takes so damn long time for it to startup gnome ?
Its not and with my firewall, cuz with only ifconfig and route
it takes so long time too around 5 mins.

What should i do?


Thank you

---

### Post by DaveBorealis on 2006-10-22
If you'd like to try an experiment, put '&' after each of your commands in '/etc/rc.local' and see if that'll run the processes in the background while the bootup continues rather than stopping the show.

e.g. ifconfig <whatever> &

A second option is to run each command one at a time to determine the slowpoke, then find out why it's taking so long so that it can be fixed.

Best regards,
Dave

---

### Post by dmsn on 2006-10-22
cool

ifconfig <...> & 

worked fine :)
but when i did 2
lines


ifconfig ,,, &
route add ,,, &

then it doesnt work anymore =/

---

### Post by DaveBorealis on 2006-10-22
Why don't you post the exact code.  I wonder if the hangup isn't with that 'route add' command.  If you're doing anything that might involve doing a DSN lookup, then it could be as simple as adding the domain to the /etc/hosts file.

---

### Post by dmsn on 2006-10-22
iconfig eth0 192.168.0.5 up &
route add default gw 192.168.0.1 &

its no problem to run that evrey time i reboot manuell.
But when rc.local do it its totaly hang up.

---

### Post by DaveBorealis on 2006-10-22
> **dmsn said:**
> iconfig eth0 192.168.0.5 up &
route add default gw 192.168.0.1 &

its no problem to run that evrey time i reboot manuell.
But when rc.local do it its totaly hang up.

I'm about out of suggestions.  If eth0 has already been brought up during the boot process, then you could try bringing it down first.  Or eth0 might be in use (e.g. ntp) and the kernel won't bring up the new IP and gateway until done with the first.  In which case you might have to approach the problem from another angle or live with it.

Sorry,
Dave

---


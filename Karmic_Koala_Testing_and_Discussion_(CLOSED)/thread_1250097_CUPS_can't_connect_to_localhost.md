---
title: "CUPS can't connect to localhost"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rogerdean on 2009-08-26
Hello all

I've just noticed that my printing is down, with CUPS reporting that it can't connect to localhost. When I try to connect manually via "System -> Administration -> Printing" I get -

There was an error during the CUPS operation: 'httpConnectionEncrypt failed'

I can't remember when printing last worked, but certainly within the last 3 days

Anyone else getting this?
Cheers
Roger

---

### Post by bgold2005 on 2009-09-08
Same with me. I made the mistake of trying
sudo aa-enforce cupsd

and now when I go to sstem->Administration->Printing Server->Connect
it just crashes immediately and window dissappears w/o message

(this is on the higher version of koala, have to try the lower version
[upgrade installed two versions on my notebook])

any fixes out there?
any way to reverse my enforce command (whatever that is)

thanks

---

### Post by pulpo69 on 2009-09-08
sudo mv /etc/cups/cupsd.conf.O /etc/cups/cupsd.conf
sudo service cups restart

---

### Post by sceptre0 on 2009-10-02
Thanks pulpo69.  I can finally print again.

---

### Post by kstarkey1 on 2009-10-27
> **pulpo69 said:**
> sudo mv /etc/cups/cupsd.conf.O /etc/cups/cupsd.conf
sudo service cups restart

I'm having a very similar issue.  No printing issue until a couple of days ago.  If I run 'sudo service cups restart', then everything is great.  If I reboot, then no printing until I run 'sudo service cups restart' again.  I'd hate to have to hack something to get this to work.  I'd rather just fix it if I can.

Anyone have any ideas?

Thanks!

---

### Post by kstarkey1 on 2009-10-28
I guess for now I'll just have to hack a solution :(

---

### Post by kstarkey1 on 2009-10-28
I created a little two line bash script to restart the cups service and an icon on the desktop that runs it.

Anyone know if a future update might fix this, or does anyone have any more ideas I could try?

thx

---


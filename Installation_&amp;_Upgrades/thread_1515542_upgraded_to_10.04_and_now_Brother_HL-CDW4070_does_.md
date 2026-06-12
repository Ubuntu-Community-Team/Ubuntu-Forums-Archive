---
title: "upgraded to 10.04 and now Brother HL-CDW4070 does not work"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by MotorBene on 2010-06-22
I just upgraded to 10.04 from 8.04.  My Brother laser printer HL-CDW4070 no longer prints. The printer did survive a previous upgrade.

Several other users have had this problem for other printers, but the fixes look to be brand specific. I hesitate to reinstall the LPR and CUPS without first knowing whether there's an easier fix.

Error message from evince on a pdf file:
Print Error
There was a problem processing document 'R Graphics Output'

Retried with another file ... and it hung. Retried from xpdf and it 
queued behind the one that hung.

Maybe related:
 - flash plugins were in a bad state.  I followed advice from another post and got it fixed.
 - synaptic shows hl4070cdwcups and hl4070cdwlpr both installed with the latest version
   which is 1.0.0-7 .... but they're listed as size 0 B  (properties says size is N/A)
 - I reinstalled cups-pdf which was missing/broken and restarted the computer but still no luck
 - power cycled the printer, tried again, still no luck

---

### Post by MotorBene on 2010-06-24
I wrote to Brother and they pointed me to the following page:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090)

That worked and it was easier to do than the previous installation that 10.04 clobbered.

At one point the installation asks:
Will you specify the Device URI? [y/N] ->
I chose N, thinking that a device URI was only
for network printers, mine was on USB, and I
might not be able to provide a valid one.  

It is working for me, but other people might want
to look up device URIs before starting the intall.
The process ends with a complaint by AppArmor
which may be due to not providing an URI.

---


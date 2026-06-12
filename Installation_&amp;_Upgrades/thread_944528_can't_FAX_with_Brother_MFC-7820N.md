---
title: "can't FAX with Brother MFC-7820N"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by TimDaniels on 2008-10-11
My Brother multi-function printer can print and scan with Ubuntu,
but it can't FAX.  It can dial out when directed by command line,
e.g. "brpcfax testdoc.txt", but what it sends is endless blank
pages.  The same happens when directed by OpenOffice.  (The unit
works just fine with WinXP and Vista.)

It can FAX a .ps file fine, but .pdf files cause the printer to
report an "out of memory" error.

Besides pointing out the illegality of using the FAX function in
the U.S. (because it doesn't add a header that identifies the
sender), the Brother Japanese customer support hasn't been able
to figure out what's wrong despite a 2-week long "chat".

Has anyone out there gotten the Brother MFC-7820N (network-
attached multi-function printer/scanner/FAX) to FAX with
Ubuntu 8.04?

*TimDaniels*

---

### Post by crazyness003 on 2009-01-07
hi. im not gonna be much of help. but how did you get to fax using your mfc? I have the brother BRFAX device installed via cups. And i can also direct printing to BRFAX...but then nothing happens. Its like im sending my faxes to /dev/null. 
I select print to BRFAX and it says "printing" then nothign happens. It dosnt ask me for a fax number, or anything.

I've tried using efax-gtk and gfax, but i think i'm taking the wrong approach.
I dont mind sacing everythign in a .ps file to fax later, i just need to be able to fax without fisrt printing, since i fax A LOT (this would kill my paper budget)

EDIT: I just tried it again and it hung my OOo session. Am I missing anything?

---

### Post by thetester on 2009-01-12
:( Same problem here. E.g. from openoffice - the fax dails the number and sends the exact ammount of pages - but all of them blank...
I don't know how to fix that. Printing, scaning with xsane works fine.

---

### Post by FiReSTaRT on 2010-10-28
I got my hints from here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_pcf.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_pcf.html) even though I haven't tried actually faxing anyone, at least it dials out. 
Save as .ps, right-click on the file in Nautilus, Open With, Other Application, enter the command "brpcfax -P BRFAX -o Paper=Letter". 
It looks like direct printing is not possible. I'll dig into it a bit more.. Might be a manual config tweak that would allow for you to do it directly, but don't hold your breath.

P.S. Using an MFC-7440N, on Maverick AMD64 (as if any of that mattered)

Edit: I couldn't find any other viable solution, so it's basically insert cover page, print to ps (I'd save it in a faxing folder), open with brpcfax and dial.

---


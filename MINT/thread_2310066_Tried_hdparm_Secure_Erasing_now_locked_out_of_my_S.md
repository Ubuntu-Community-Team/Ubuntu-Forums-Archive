---
title: "Tried hdparm Secure Erasing now locked out of my SSD"
date: 2016-01-15
forum: MINT
---

### Post by msprinnydancer on 2016-01-15
Hello. I am hoping someone has experience with the Crucial M4 SSDs. I  attempted to secure erase an SSD using the hdparm command however I did  something incorrectly and now whenever I boot up the ssd I get a lock  symbol+HDD on my Thinkpad X201. So far I have removed the M4 from the  X201 and placed it in my desktop. It is still Master Password locked and  I am at my wits end! I just bought this second hand from ebay and was  going to use it in my X201 and give the current SSD in the x201 to a  family member. I am not sure what to do.

I tried issuing an: sudo  hdparm --security-disable PWD but that does not work. I attached a  screenshot of what I see in terminal (using a LiveUSB of Linux Mint). I  have never had a problem with secure erasing any of my SSDs and this is  the first time an issue popped up. TIA.

**EDIT:**

I think I figured it out. Will verify in a minute as I move the SSD back to my X201 and attempt to restore an image I saved earlier this week via Macrium Reflect.

Edit:

Okay I figured it out. I figured out how to disable the Master password however I am not sure what I did not do correctly executing a procedure I have done > 10 times. The command to disable the password needed to include a previous temp password+ /dev/sda to follow through with disabling security. My Macrium Reflect image transferred nicely over to the M4. It is running great so far!

---


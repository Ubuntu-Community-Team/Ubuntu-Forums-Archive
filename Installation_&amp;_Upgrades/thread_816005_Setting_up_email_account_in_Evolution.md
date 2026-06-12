---
title: "Setting up email account in Evolution"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by Terry Owen on 2008-06-02
Just installed Ubuntu - first try with Linux!

All working fine except email! 

Have set up the account using the same settings as I've used before on another OS. I can receive email OK but I can't get send to work. Using POP to receive and SMTP to send. Done this many times for different accounts across different machines with no probs.

Anyone experienced similar problems? I'm stumped!

Ubunto version 7.10
Evolution version 2.12.1

---

### Post by lisati on 2008-06-02
You might want to click on the "check for supported types" when setting up the servers.

---

### Post by Kevbert on 2008-06-02
What email accounts are you using ? Hotmail, gmail, yahoo ?

---

### Post by wpshooter on 2008-06-02
Who is your ISP that is servicing your e-mail ?

If it is someone like Verizon DSL or similar perhaps I can help you.

---

### Post by Terry Owen on 2008-06-02
Hi,

Thanks for the responses.

I'm bases in Norway, using an account from one of the Telephone companies here. Been using it for 5 years or more with no probs.

I've also tried setting up a gmail account but that does the same. 

Clicked on the button to check for supported types but got no response.

Have also installed Ubunto on a laptop, tried setting up email on there and have the same result.

Bit of a mystery this one.

---

### Post by wpshooter on 2008-06-02
Terry:

I assume that you are absolutely confident that you have the correct parameters in the incoming and outgoing fields per your ISP !!!

If you don't have the correct parameters setup in these fields you are probably not going to get any response when you poll for the supported types.

Also, are you certain about the e-mail address and password that you are using for the account !!!

---

### Post by Terry Owen on 2008-06-02
Jupp!

Checked, double-checked, triple-checked. Tried all combinations of the various options but still nothing. It is all so straightforward I can't fathom where I could go wrong.

The things I'm not sure about is authentication, assuming the following:-

PLAIN - no username or password required
Login - with my account name and pwd
POP before SMTP - is this something to try?

Tried all three but perhaps I need these in conjunction with some other options.

My server requires authentication, tried switching it off on other setup and it failed, enabling it again and it works.

Still stumped.

---

### Post by wpshooter on 2008-06-02
Unfortunately, I am at work now and don't have my Evolution machine in front of me but to the best of my recall I use the PLAIN for the SMTP (sending) function and I do put in my email address and do check the password box at the bottom of the SMTP page.  And I don't think that my Verizon DSL requires authentication, so I leave this unchecked.

Is this some type of high speed ISP or is this a dialup account that you are working with ?

P. S. - When you are putting in the e-mail are your putting in the COMPLETE e-mail address including the ISP name ?

---

### Post by Kevbert on 2008-06-02
One thing you may want to try is setting the port as some email clients use non standard port numbers (something like smtp.my_email.com:997 where 997 is the port number).
If the supplier is someone like Telia then there should be something on the web or even their website on how to set up a mobile phone to receive email, that may give you a hint.

---

### Post by Dougie187 on 2008-06-02
No offense, but you obviously dont have the right settings if your gmail isnt working. Unless there is some issue with your ISP blocking some ports for some reason (i guess its not that uncommon). Either way, just to check your gmail settings here is their instructions on how to set up evolution for checking gmail.

[http://mail.google.com/support/bin/answer.py?answer=13287&topic=12917](http://mail.google.com/support/bin/answer.py?answer=13287&topic=12917)

I used this in evolution and it worked fine for me.

---

### Post by yogo on 2008-06-02
> **Terry Owen said:**
> Jupp!

Checked, double-checked, triple-checked. Tried all combinations of the various options but still nothing. It is all so straightforward I can't fathom where I could go wrong.

The things I'm not sure about is authentication, assuming the following:-

PLAIN - no username or password required
Login - with my account name and pwd
POP before SMTP - is this something to try?

Tried all three but perhaps I need these in conjunction with some other options.

My server requires authentication, tried switching it off on other setup and it failed, enabling it again and it works.

Still stumped.

Just a guess, but Evolution asks you to use smpt.server.com  for outgoing but I use mail.server.com and that works.. Replace server.com with your parameters.

---

### Post by Terry Owen on 2008-06-02
I guess it's a high speed ISP, we have a 4Mbit broadband connection.

Still working through the combinations but I think there is something else going on here. Set up a google mail account too, recieved mail but won't send.

---

### Post by yogo on 2008-06-02
Here is how sending is set up on mine, see screenshot.

---

### Post by wpshooter on 2008-06-02
Why don't you call the ISP and ask them what their outgoing mail server name is.  For instance for Verizon it is:  outgoing.verizon.net

---

### Post by Terry Owen on 2008-06-03
I've just used the same as I've used before. Still reading mail with outlook, have configured exactly the same but still it won't work.

Out of ideas now. Gmail does the same thing, must be something with the way Ubuntu is handling outgoing email.

Thanks for all the responses.

---

### Post by Terry Owen on 2008-06-03
> **Kevbert said:**
> One thing you may want to try is setting the port as some email clients use non standard port numbers (something like smtp.my_email.com:997 where 997 is the port number).
If the supplier is someone like Telia then there should be something on the web or even their website on how to set up a mobile phone to receive email, that may give you a hint.

It looks like this is my problem, ISP did change the port number.

Where do I check/change this?

---

### Post by Kevbert on 2008-06-04
Just add the number with a colon onto the end of the server address. Select Edit - Preferences (Select account name) - Edit.  Now go to Sending Email tab and under Server Configuration - Server add a colon and the new number.

---

### Post by lisati on 2008-06-04
Some email providers (including Gmail and Yahoo) require you to log into their webmail service and enable POP access.

---

### Post by FashionablyLate on 2008-06-15
I'm struggling to get my hotmail account to work in evolution.
I followed instructions in another thread and set the receives and send servers names to localhost:2000 and 127.0.0.1:2500 respectively. I can receive mail ok (registered here and collected mail without issue) but I can't send mail. I sent a test message and it just sits in the outbox.
I've tried downloading freepops and the updater but didn't actually do anything with them after download as I didn't know what I needed to do!

Any advice on how to get the sending funtion working would be most welcome.

---

### Post by rkosby on 2008-06-24
I've had trouble with Evolution ever since installing Hardy Heron.  I've used it for years prior.  It can't send email either.  I noticed it keeps trying unsuccessfully to use the gnome-keyring.  Could you be having the same problem?  

Also, now I have to use the evolution --force-shutdown to bring it down.

---

### Post by ibgeorgeb on 2008-07-26
This works Dougie187, neat. I didn't have view pages of pics to get Evolution to sync with my gMail. ibgB-)

---


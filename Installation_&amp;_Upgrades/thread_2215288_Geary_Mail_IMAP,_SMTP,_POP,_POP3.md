---
title: "Geary Mail: IMAP, SMTP, POP, POP3?"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by Smallwheels on 2014-04-05
I'm trying Geary Mail. Gmail setup was a breeze because all it required was my address and password. I have a live.mail.com address too. In the Geary setup there are choices for Gmail, Yahoo, and Other. I'm going with Other. 

When I select Other, two more fields appear. One says IMAP and the other says SMTP. When I fill in my e-mail address in the top field of the three sections it auto-populates the IMAP and SMTP sections that ask for e-mail address.

When I went to my other computer to get the configuration information I see that it uses SMTP for the outgoing mail server and the incoming server is POP3.live.com. Where do I input that information? Do I put that in the IMAP section? 

Geary mail also has port numbers in each section. They are pre-populated but how do I know if they are correct? I just need to know what information to put into each box. I think I've got the SMTP section handled, other than the port number. 

There are also boxes for me to enter the password. There is one in the IMAP section and one in the SMTP section. I didn't know there could be different passwords for incoming and outgoing messages. Maybe there aren't. I tried just filling in the SMTP section without doing anything in the IMAP section and the apply button wouldn't become click-able until I entered information into all of the fields on the page. 

To somebody who has a clue this should be easy. Unfortunately I'm to inexperienced at this to make it work. 

Thank you for your help.

---

### Post by buzzingrobot on 2014-04-06
Mail that you *receive* is handled by either an IMAP or a POP mail server. (IMAP and POP are two different protocols for mail delivery). The mail server you use will have a unique name, very often beginning with "imap" or "pop". 

Mail you *send* is handled via SMTP.

 You need to check the settings/help page page of your mail provider to find out their server names and the ports the servers use. That name is not your email address, although Geary may be able to identify the correct server from your mail address, and then lookup the correct server names and port numbers and pre-populate them.

You will know if Geary pre-populates fields correctly if you can send and receive mail.  If not, Geary got it wrong.

IMAP servers and POP servers are different.  Don't plug in an IMAP server name when POP is requested, or vice versa.

The server names and port numbers remain the same on any computer where you use the same mail account.

Most people create both outgoing (SMTP) and incoming (IMAP or POP) accounts with the same mail provider and set up a single password for both when they do that.  However, you can use one provider for outgoing mail and another provider for incoming mail, and, if you wish, create two different passwords.

If Geary is working fine, then it's been set up correctly.  If not, find out the server names and ports your mail provider uses and enter them in Geary's account setup panel.

Geary is a relatively new app that, I believe, initially knew how to handle only Gmail accounts, but has begun to enable others.  You'd need to check the Geary site for the capabilities of your specific version.

---


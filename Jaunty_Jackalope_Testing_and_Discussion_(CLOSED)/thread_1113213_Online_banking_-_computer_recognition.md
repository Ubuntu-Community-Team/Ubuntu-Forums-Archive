---
title: "Online banking - computer recognition"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kaibob on 2009-04-01
I use online banking. It allows me to directly log-in to my bank account only if it recognizes my computer. If the online banking does not recognize my computer, additional steps are required.

With Hardy, the online banking recognized my computer and I had no problems. After upgrading to Jaunty, the online banking does not recognize the computer. I've worked with the bank and tried everything we could think of at their end and with my computer but it just doesn't work.

Is there something new in Jaunty that would prevent the online banking from recognizing my computer? Perhaps some new security measure?

Thanks!

---

### Post by phenest on 2009-04-01
How do they 'recognize' your computer? Is it through an IP ar MAC address?

---

### Post by philinux on 2009-04-01
Get the user agent switcher and set it to mimic IE7. 

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by psyke83 on 2009-04-01
> **kaibob said:**
> I use online banking. It allows me to directly log-in to my bank account only if it recognizes my computer. If the online banking does not recognize my computer, additional steps are required.

With Hardy, the online banking recognized my computer and I had no problems. After upgrading to Jaunty, the online banking does not recognize the computer. I've worked with the bank and tried everything we could think of at their end and with my computer but it just doesn't work.

Is there something new in Jaunty that would prevent the online banking from recognizing my computer? Perhaps some new security measure?

Thanks!

Most online banks use either a secure Java/ActiveX applet, or a Mozilla plugin.

Ensure that you've installed the latest Sun JRE and browser plugin from the repository (and remove other JRE implementations, as they may be incompatible).

Your bank may use a Firefox plugin which is "hardcoded" to install only if the browser reports your OS version as the Hardy release.

If that doesn't help, give some more details so we can help.

---

### Post by kaibob on 2009-04-02
Thanks for the responses.

I asked about the computer recognition, and the tech-support woman was a bit vague but said that the online banking recognizes physical and software aspects of the computer. It sounds something like the Windows verification. If the online banking does not recognize your computer, you have to enter a code sent to you cell phone in a text message or, as an alternative, you have to answer a number of questions that you had previously answered (e.g. your city of birth). 

I checked the Sun JRE. It is current and there are no earlier version installed. There are two Java programs shown in Synaptic: sun-java6-bin and sun-java6-jre. I assume both are needed. The Firefox Java plug-in is version 1.6.0_13, which is the version installed by Jaunty. I tried the the Firefox extension, but it didn't work either. 

For now, I'll use the lengthier log-in process and consider going back to Hardy, which worked fine with the online banking.

Thanks again. 

kaibob

---

### Post by sgosnell on 2009-04-02
I always assumed the recognition was done by a cookie.  Do you have firefox set to allow cookies?  My banks (I use 4 of them) all recognize my computers on Jaunty, so I don't think it's a problem with Jaunty.

---

### Post by kaibob on 2009-04-03
I thought I would leave a final comment on this thread just in case someone with a similar issue happens upon it.

Despite a lot of time and effort, I was never able to resolve this issue, so I restored the most current drive image of my Hardy install. I logged onto my bank site, and it recognized the computer and allowed me to continue without further issue. Why this works with Hardy and not Jaunty is a mystery. I did learn that the Bank site uses JavaScript to recognize the computer. Perhaps there is a difference between the JavaScript used with Jaunty and that used with Hardy. The settings were the same.

---

### Post by mykrob on 2009-04-03
My i ask what bank?

My bank does the same thing, but I have the option of them sending a randomly generated password to the email on file, i them check my email and enter that password from the computer I want to authorize, then it works.

I am able to log onto both my banks from Jaunty just fine.

---

### Post by kaibob on 2009-04-04
> **mykrob said:**
> My i ask what bank?

My bank does the same thing, but I have the option of them sending a randomly generated password to the email on file, i them check my email and enter that password from the computer I want to authorize, then it works.

I am able to log onto both my banks from Jaunty just fine.

My bank has a similar option--you enter your normal ID and password and you then have to enter an additional randomly-generated password that is sent as a text message to your cell phone. I don't have a text-message plan and don't want to pay the per-text-message price (retired and fixed income). If the bank site recognizes your computer, the second password is not required.

---

### Post by bennachie on 2009-04-04
> **kaibob said:**
> It's Bank of America. They have an option somewhat similar to what you mention--you enter your normal ID and password and you then have to enter an additional randomly-generated password that is sent as a text message to your cell phone. I don't have a text-message plan and don't want to pay the per-text-message price (retired and fixed income). If the bank site recognizes your computer, the second password is not required.

That's very annoying for you, but the problem does not seem to be a general one. I can access both my Australian bank account and my NZ account without any difficulty, apart from the inevitable initial message suggesting that my user experience would be improved if I moved to the latest version of IE. That recommendation is so far removed from reality - I have checked on my Windows machine - that it is hard to repress a smile. The message is bypassed by means of a cookie for all subsequent logins, but I'm pretty sure that cookies play no other role in the login process.

---


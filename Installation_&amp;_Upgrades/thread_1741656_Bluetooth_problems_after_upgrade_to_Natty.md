---
title: "Bluetooth problems after upgrade to Natty"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Erwin Van de Velde on 2011-04-28
Hi all,

I upgraded to Natty and ever since I have the following problem:
After booting, the bluetooth adapter is not found by the system even though the bluetooth service is running. Restarting this service fixes this issue.
Another issue though is that my Apple Mighty Mouse is found and paired, but can only move and scroll, no clicks are registered (tested also with xev).

What can I do?

Thanks in advance!

---

### Post by mörgæs on 2011-04-28
How does the machine work in a live boot?

---

### Post by nadeepa on 2011-04-28
> **mörgæs said:**
> How does the machine work in a live boot?

Same problem here. Bluetooth works fine in a live boot. Worked in Maverick too.

---

### Post by Erwin Van de Velde on 2011-04-29
Live boot seems okay too

---

### Post by mörgæs on 2011-04-29
Then I would do a fresh installation. This kind of problems is not uncommon to an upgrade.

---

### Post by bertilow on 2011-04-29
> **mörgæs said:**
> Then I would do a fresh installation. This kind of problems is not uncommon to an upgrade.

I have the exact same problem, but I did a fresh install of Natty. It has now become a habit to restart the computer at once after a cold boot, otherwise my bluetoth mouse can't be used. A bit annoying.

---

### Post by mörgæs on 2011-04-29
What about Erwin and Nadeepa? Do you also have the problem in a fresh install?

---

### Post by nadeepa on 2011-04-29
> **mörgæs said:**
> What about Erwin and Nadeepa? Do you also have the problem in a fresh install?

I didn't tried a fresh install yet. I can live with small glitch in bluetooth for a while.

Will do a fresh install in couple of weeks and see.

---

### Post by locluca on 2011-04-30
Hello everybody, I did a fresh install of Natty and I have the same problem. It says Bluetooth is off and when I go to Bluetooth>Preferences and I click on "Turn it on" it just crashes. Any guess? Thanks :)

---

### Post by jabryl on 2011-04-30
Experiencing a similar problem. Bluetooth worked the first time I booted after the Natty upgrade but hasn't worked since.

When I plug the adapter in the Bluetooth icon appears in the panel but when I click "Turn on Bluetooth" nothing happens.

---

### Post by mörgæs on 2011-05-01
This seems to be a general problem. Best is to open a bug report:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by compuguy1088 on 2011-05-01
> **mörgæs said:**
> This seems to be a general problem. Best is to open a bug report:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

A bug report has been opened for this particular bug: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964)

I can confirm that this is still an issue. This occurs for me when bringing my Dell D620 out of suspend.

---

### Post by henrodon on 2011-05-02
> **mörgæs said:**
> This seems to be a general problem. Best is to open a bug report:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
Has anybody reported this bug yet? I started the process, but got referred to an application called apport, which I can't find. The specifics in my case are that, after upgrade, bluetooth worked, but today (the next day) it only worked at first. After a re-start, I get the bluetooth icon with a little red x, but when I click it, Bluetooth is apparently on9 "Bluetooth On" is grayed out and "Turn off Bluetooth" is an option. I've tried turning it off and then back on, but it doesn't seem to truly turn on because I'm not given the option of connecting my headset and the little red x still apprears as part of the icon in the top pane (what used to be called the panel).

I hope someone has reported the bug.

---

### Post by mörgæs on 2011-05-02
Did you read the post above before posting?

---

### Post by locluca on 2011-05-03
Hello everyone, when I updated natty today the problem was solved and I can connect my nokia to natty!!!:) Hope this could help you. Try to update and install even the "natty-proposed" (for instance I upgrade the kernel from 2.6.38-8 to 2.6.38-9). Bye

---

### Post by ianp5a on 2011-05-03
Yes!
Same Problem: After Natty, no bluetooth mouse
Same solution: Update Manager. Restart. Problem fixed.
 Thanks!

Edit: But it seems the Bluetooth Mouse has to be switched on a boot.

---

### Post by Peppercorn on 2011-06-14
Same problem here! Is there any way of fixing this yet??

---

### Post by locluca on 2011-06-21
Try to update (make sure that you upgrade the kernel too, select "natty-proposed" on "update manager", "settings") and the problem should be solved.

---


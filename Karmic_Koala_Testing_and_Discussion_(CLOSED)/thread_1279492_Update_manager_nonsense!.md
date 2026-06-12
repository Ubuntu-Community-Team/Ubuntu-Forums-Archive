---
title: "Update manager nonsense!"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-09-30
Where does a person report nonsense? The previous update manager dialog was perfectly adequate for the job that it did, why change it to something inferior?
It now requires mental arithmetic on two 4 or 5 digit numbers to get the downloaded progress amount, and a total guess as to the download rate. What a mess.

Suggestions:
Remove the unnecessary icon.
Report downloaded data as a percentage.
Ensure that the download speed fits within the text box.

---

### Post by hanzomon4 on 2009-09-30
I like the new way

---

### Post by FuturePilot on 2009-09-30
I kind of like the icon, but I agree with the other points. You might want to file bug reports on those if they haven't been filed already.

---

### Post by coldReactive on 2009-09-30
I kind of like the icon too, as well as the points you mentioned.

---

### Post by Slug71 on 2009-09-30
I too like the icon but not the behaviour.

---

### Post by bluenova on 2009-10-01
I understand why they have had to change the underlying code, but I agree there was nothing wrong with the old UI so it could have been used as a template for the new version rather than re-inventing the wheel.

---

### Post by forumache on 2009-10-01
> **mdurham said:**
> Where does a person report nonsense? 

Here: [https://bugs.launchpad.net/ubuntu/karmic](https://bugs.launchpad.net/ubuntu/karmic)

And then you provide the link for the bug for people to subscribe to it/this bug affects me too or just comment, until it reaches the "confirmed" state.

Then we wait for some developer to pick it up and fix it.

Easy...

---

### Post by rajeev1204 on 2009-10-01
I too dislike the new changes to update manager except the one where it doesnt ask for password to check for updates.Otherwise,the icon is broken for me,and the window doesnt give proper information and i cant resize it to see the full message.

---

### Post by steeleyuk on 2009-10-01
> Report downloaded data as a percentage.

Avoid.

[QUOTE="Human Interface Guidelines"]The progress bar text should provide an idea of how much work has been completed. It is better to provide specific information rather than a unitless percentage. For example, "13 of 19 images rotated" or "12.1 of 30 MB downloaded" rather than "13% complete".[/QUOTE]

---

### Post by steeleyuk on 2009-10-01
Filing bugs at Launchpad has changed slightly. Trying to encourage the use of Apport, directly from the application rather than manually filing in the information.

> If for some reason you cannot file a bug through the Apport tool you can file one via Launchpad. When doing so please ensure that you have determined which package it should be filed against. Read 'finding the right package' for guidance or use Launchpad's package search feature. To file a bug against a specific package use a url similar to the following, [http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect](http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect), where PACKAGENAME is the name of the source package about which you want to file the bug. In the event that you want to request a piece of software be packaged for Ubuntu please follow the instructions in the wiki. 

---

### Post by taavikko on 2009-10-01
> **Chauncellor said:**
> Every time I try and open a bug in Launchpad, I'm directed to this page:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

what the hell?

did you read what it says....
It's there for a purpose.

---

### Post by go7Ul1ai on 2009-10-01
> **Chauncellor said:**
> Yeah, one of the first things it said to me was:

"Ubuntu uses Launchpad to keep track of bugs and their fixes. To file a bug you first need to create an account."

It confused me.

How does that confuse you? It's saying that you need to create an account on Launchpad before you're able to file a bug :S

---

### Post by mharrison on 2009-10-01
> **lee.jarratt said:**
> How does that confuse you? It's saying that you need to create an account on Launchpad before you're able to file a bug :S

My sarcasm detector has overloaded captain...

---

### Post by go7Ul1ai on 2009-10-01
> **mharrison said:**
> My sarcasm detector has overloaded captain...

It's hard to detect sarcasm through text.

---

### Post by mpt on 2009-10-01
> **mdurham said:**
> Where does a person report nonsense? The previous update manager dialog was perfectly adequate for the job that it did, why change it to something inferior?

In Karmic, Michael Vogt ported Update Manager to use Aptdaemon when available instead if Synaptic. Aptdaemon’s use of PolicyKit is more secure than Synaptic’s use of gksu. I think, though I’m not sure, this means Aptdaemon also takes over the task of showing progress feedback, and it needs a bit of design improvement.

Meanwhile, I wanted to redesign Update Manager thoroughly for Karmic, but I was too busy with the Ubuntu Software Center and other design work. I plan to specify this thoroughly for Lucid — using no separate progress windows at all, but rather showing progress in the main updates window.

> [i]Suggestions:
Remove the unnecessary icon.[/i]

Agreed. It doesn’t add anything, and it makes the progress window look unnecessarily similar to an alert.

> *Report downloaded data as a percentage.*

That would be a bit redundant. Showing the proportion complete is what the progress bar is for.

> *Ensure that the download speed fits within the text box.*

[Bug 434937]("http://launchpad.net/bugs/434937").

---

### Post by mdurham on 2009-10-01
Thanks for the info mpt, I guess we're stuck with this for the next few months :(
Cheers, Mike

---

### Post by olskar on 2009-10-01
> **mpt said:**
> i plan to specify this thoroughly for lucid — using no separate progress windows at all, but rather showing progress in the main updates window.




+1!

---


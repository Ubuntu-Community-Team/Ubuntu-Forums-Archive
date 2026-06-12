---
title: "reporting bugs"
date: 2009-02-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by josephellengar on 2009-02-01
Hi.  I've been playing around with the jaunty alpha just for fun, and I was wondering if the developers get my bug reports when I send the crash if I don't make a launchpad entry?  I've made some entries but it crashes and I always send the automated report, but sometimes I don't have time to make a launchpad entry as well.  thanks!

---

### Post by UbuWu on 2009-02-01
No, they don't. The automated crash report is attached to the bugreport if you complete it.

---

### Post by Slug71 on 2009-02-01
> **UbuWu said:**
> No, they don't. The automated crash report is attached to the bugreport if you complete it.

Correct. You must have a Launchpad account to complete the bug report.
If you cant create one then you really shouldn't be using Jaunty at this point.

---

### Post by josephellengar on 2009-02-01
oh.  Thanks. :(

---

### Post by Gina on 2009-02-02
What's the problem with creating a launchpad account?

---

### Post by josephellengar on 2009-02-02
Nothing.  Just that I thought I was helping the developers when I created the report even if I didn't make a launchpad entry.

---

### Post by Gina on 2009-02-02
Fair enough.

---

### Post by Gourgi on 2009-02-02
is there a way to attach the automatic created report to an existing bug i have subsccibed ?
i mean when the automated report is created, firefox opens to submit a bug and if one sees that the bug is already reported then he subscribes himself to the bug. but where does the report goes?
wouldn't be usefull to be attached to the subscribed bug?

---

### Post by Slug71 on 2009-02-02
Yes if someone else has already submitted it then you can subscribe to that one.
If you dont subsrcibe or have a launchpad account, its just like closing a webpage.

---

### Post by Slug71 on 2009-02-02
> **idigchess said:**
> Nothing.  Just that I thought I was helping the developers when I created the report even if I didn't make a launchpad entry.

I did the same thing when i started testing with Intrepid.

---

### Post by dinxter on 2009-02-02
apport automatically collects crash data and reports them to launchpad (i think it now defaults to private until reviewed to not expose any possibly sensitive data?), no separate launchpad bug opening is necessary. you could of course instead file a bug and attach the relevant crash file from /var/crash if you like

---

### Post by chrisccoulson on 2009-02-02
> **dinxter said:**
> apport automatically collects crash data and reports them to launchpad (i think it now defaults to private until reviewed to not expose any possibly sensitive data?), no separate launchpad bug opening is necessary. you could of course instead file a bug and attach the relevant crash file from /var/crash if you like

No, please don't attach the crash file. The retracers can't handle that and it requires a lot more effort to actually extract the useful information from them. Most triagers will just close the report and ask you to submit it properly using Apport if you do that.

And as already pointed out, when using Apport to submit a crash report, you **must** complete the bug report entry in Launchpad. Once you have completed it, the information from your crash file will be automatically attached to the report.

---

### Post by Gourgi on 2009-02-02
i know that apport automatically collects crash data and reports them to launchpad when i complete my _new_ bug report.
what i'm asking is how can i reproduce apport's (mini or full) report to manually attach it to an existing bug report that another user reported?
where i can locate this report in my computer ? /var/crach ?

also would attaching apport's bug report be usefull for the developer to fix the bug easier?
he'd have more than 1 crash reports for the same problem to compare so it is usefull , right ?

---

### Post by tawmas on 2009-02-02
> **Gourgi said:**
> i know that apport automatically collects crash data and reports them to launchpad when i complete my _new_ bug report.
what i'm asking is how can i reproduce apport's (mini or full) report to manually attach it to an existing bug report that another user reported?
where i can locate this report in my computer ? /var/crach ?

There seems to be no way to do that. I was suggested the following workaround on IRC: open a new bug, mark the new bug as a duplicate of the existing one, add a comment to the old bug saying "Apport-generated crash data in duplicate bug #NNNNN".

This is only useful if the existing bug doesn't already have apport generated data attached (see below).

> **Gourgi said:**
> also would attaching apport's bug report be usefull for the developer to fix the bug easier?
he'd have more than 1 crash reports for the same problem to compare so it is usefull , right ?

mmm... As far as I know, the relevant information would be exactly the same, so there's litle point submitting duplicated apport crashes.

---

### Post by Gourgi on 2009-02-02
> **tawmas said:**
> There seems to be no way to do that. I was suggested the following workaround on IRC: open a new bug, mark the new bug as a duplicate of the existing one, add a comment to the old bug saying "Apport-generated crash data in duplicate bug #NNNNN".

This is only useful if the existing bug doesn't already have apport generated data attached (see below).

ok thanks for clearing that out
i'll have it in mind

---


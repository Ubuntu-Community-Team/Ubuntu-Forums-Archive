---
title: "Does Anyone know if there is a fix coming for Evolution?"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by grubdude on 2010-03-05
Hi,

Using Evolution and it is constantly getting stuck trying to pull down IMAP email from server. This locks up the application and it will not even close. Also forces the processor to run in the high 90s.


I have tried same email accounts with evolution on another machine using a different OS and all is working fine. It also works fine on 9.10. So, something in Lucid is causing this...Has anyone else noticed this? Very annoying as my fan starts going crazy, too....Thanks.

---

### Post by Technoviking on 2010-03-05
Have you filled a bug?

If not, type the following at the command line.
```
ubuntu-bug evolution
```

T-V

---

### Post by grubdude on 2010-03-05
Thanks will do......

---

### Post by nystire on 2010-03-06
Could you post a link to your bug? I may be having the same problem.

---

### Post by moviemaniac on 2010-03-06
me and my brother experience the same problem too on e-mail download (regardless whether it's pop or imap)

---

### Post by garba on 2010-03-06
> **grubdude said:**
> Hi,

Using Evolution and it is constantly getting stuck trying to pull down IMAP email from server. This locks up the application and it will not even close. Also forces the processor to run in the high 90s.


I have tried same email accounts with evolution on another machine using a different OS and all is working fine. It also works fine on 9.10. So, something in Lucid is causing this...Has anyone else noticed this? Very annoying as my fan starts going crazy, too....Thanks.

I had that problem myself, filed a bug report about two years ago but it looks like the problem is still there. IMAP support in Evolution is crap, period, it can't even handle folders properly. The only viable solution for the time being is apt-get remove.

---

### Post by cyberkilla on 2010-03-06
> **grubdude said:**
> Hi,

Using Evolution and it is constantly getting stuck trying to pull down IMAP email from server. This locks up the application and it will not even close. Also forces the processor to run in the high 90s.


I have tried same email accounts with evolution on another machine using a different OS and all is working fine. It also works fine on 9.10. So, something in Lucid is causing this...Has anyone else noticed this? Very annoying as my fan starts going crazy, too....Thanks.

That's strange. I use IMAP on several accounts and don't suffer lock-ups. Perhaps I'm not pulling enough emails at once to trigger it.

---

### Post by grubdude on 2010-03-06
Thanks guys...Well I have not filed bug report yet because it looked like it was working okay for quite some time and then when I looked at it this morning, my fan and processor were going crazy and it was locked up.

This is happening on pop and IMAP. The amount of email for the IMAP is not that much either.

On my Karmic it works fine, so far.

I hope they correct this or else it is Thunderbird, I guess. ;-)

---

### Post by bela42 on 2010-03-06
I've learned, that disabling all spam filters client side does help a lot. Given the excellent spam filters server side everywhere I think it is worth a try.

Before I did experience lockups since years, really.

---

### Post by grubdude on 2010-03-06
Thanks I will take a look at that....

---

### Post by cyberkilla on 2010-03-06
> **bela42 said:**
> I've learned, that disabling all spam filters client side does help a lot. Given the excellent spam filters server side everywhere I think it is worth a try.

Before I did experience lockups since years, really.

Oh, I know what you mean! I get thousands of spam messages and it hangs for a couple of minutes sorting them all when I first start Evolution.

Normally, I would filter server-side with spam-assassin, but its documentation says that it is "not recommended" and they are in favour of the client side filtering based on the spam headers it inserts.

I'd rather just have the spam dumped into a spam folder server-side, but then I'd have TWO spam/junk folders when I came to use it in Evolution. It seems like the junk folder in Evolution isn't a real folder, so you can't reassign it to another IMAP one.

But enough about my mail management problems:p

---

### Post by grubdude on 2010-03-07
This application is literally driving me nuts. I am so tired of it locking up my processor and my machine. I reported the bug and apparently so have many others.

 I hope someone cares enough to fix it or just get rid of Evolution in favor of Thunderbird or something that works reliably.

---

### Post by lancest on 2010-03-07
Evolution crashes for me while trying to import a .csv name list.
Went to Thunderbird 3 and wow is it great. If I could just figure out how to make Thunderbird the default mail client in my top menu bar- indicator applet. (Preferred Applications ain't doing it)

---

### Post by grubdude on 2010-03-07
Yes, Thunderbird 3.0.1 is very nice. I use it on a few other OSs. I was surprised that it was not chosen as default for Ubuntu.

---


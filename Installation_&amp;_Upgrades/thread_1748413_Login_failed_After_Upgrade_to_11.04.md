---
title: "Login failed After Upgrade to 11.04"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by mNil on 2011-05-03
Hi,

I upgraded to 11.04 from 10.10 2 days back. It worked fine. 

Today when I tried to log back in, it said *authentication failed*

So, I tried the usual recovery console ([http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword))
where I reset my user password successfully (Incidentally my root user is the same as my user -- it my Dell E1505).

Now, when I select *resume normal  boot *in recovery console with new password, it works. But I am logged into a console screen (not the desktop). Every time I log out of it I am prompted to log into this console screen :frown: again

Next I tried to manually restart and start ubuntu (not the recovery console). Neither the new, nor the old password works -- still get [I]authentication failed
[/I]
Can someone please help ... or point to some other thread. Am I missing something really silly?

Thanks,

mNil

---

### Post by mNil on 2011-05-05
Well, here a rather stupid way around:

Suppose my user id in "ME". In the Ubuntu log in screen 

1. Do NOT click on "ME'
2. Click on "Other'
3. Type in user id as "root"     (without quotes of course)
4. Use your root password

Still no clue why the user "ME" is showing "authentication failed" even after I reset it with faillog.

May be I should move to absolute beginner talk

---


---
title: "Software Center unexpectedly closed - Ubuntu 12.04"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by card06 on 2014-01-10
Hello Everybody
I'm using Ubuntu 12.04 and everything was working so far, nevertheless today my software center started to crash without any apparent reason. To be a bit more precise:
The Software Center only crashes when I enter the description of any software, nevertheless as long as I stay in the welcome screen everything goes well; the search of new applications also works well as long as I don't try to enter their description.

I've tried the solutions that I've seen so far in problems that look alike in this forum, nevertheless they have not worked. I even tried uninstalling and reinstalling the software center with:

```


sudo apt-get purge software-center
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install software-center
sudo dpkg-reconfigure software-center --force

```

Attached is an image of the Software Center Log. I hope it helps

Thanks in advance

---

### Post by ian-weisser on 2014-01-10
Are there any relevant .crash files in /var/crash?
Are there any relevant log entries in /var/log/syslog?

---

### Post by card06 on 2014-01-12
I reproduced the problem again to check the creation/existence of those files and here are the answers:

> **ian-weisser said:**
> Are there any relevant .crash files in /var/crash?
Yes, I look for the crash files in the folder that you said and there are 3 files related to that crash. One of them is the one from the current crash (attached), another one ends with ".upload" and the other one ends with ".uploaded".


> **ian-weisser said:**
> Are there any relevant log entries in /var/log/syslog?
yes, after I reproduce the problem, some new entries were created. I reproduced the problem around 15:30 so those are the one that were created after the problem happened. Attached you will find the file with the info.

Thanks in advance for your help and kind regards

Camo


PS: I had to change the extension of the syslog and the crash file to txt because the ubuntuforum didn't allow me to upload it with the original extension. Also I had to compress the crash file because it was more than 19KB which was the limit for that kind of file(txt)

---

### Post by ian-weisser on 2014-01-12
> ```
Traceback:
 Traceback (most recent call last):
   File "/usr/share/software-center/softwarecenter/backend/reviews/rnr.py", line 129, in _on_reviews_helper_data
     callback(app, self._reviews[app])
   File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py", line 1050, in _reviews_ready_callback
     self.reviews.configure_reviews_ui()
   File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/reviews.py", line 284, in configure_reviews_ui
     self._fill()
   File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/reviews.py", line 208, in _fill
     self.useful_votes, is_first_for_version)
   File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/reviews.py", line 467, in __init__
     useful_votes)
   File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/reviews.py", line 615, in _build
     cur_t = self._get_datetime_from_review_date(review_data.date_created)
   File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/reviews.py", line 539, in _get_datetime_from_review_date
     return datetime.datetime.strptime(raw_date_str, '%Y-%m-%d %H:%M:%S')
   File "/usr/lib/python2.7/_strptime.py", line 325, in _strptime
     (data_string, format))
 ValueError: time data '2012-05-21T09:29:24.742Z' does not match format '%Y-%m-%d %H:%M:%S'

```

Well, that's the bug. It's in the crash report.

Do you want to muck around with Python to fix it?
Or do you simply want to report the bug?

---

### Post by card06 on 2014-01-12
Well if possible both. I would like to report the bug so that they can fix it but if the fixing takes a lot of time(more than a month) I would have to handle myself without the Software Center for a long time and I certainly don't want to do that.

What do you recommend me to do?

---

### Post by ian-weisser on 2014-01-12
I recommend filing a bug report against software center
Use the command **apport-bug**** /var/crash/_usr_share_software-center_software-center.1000.crash**
The bug reporting application, apport, will fill in the rest. Easy.

The report, if it can be duplicated by a triager, will probably be low priority - a much newer version of Software Center will be in 14.04, just three months away.
Nevertheless, the problem and solution in a bug report may help others, and 12.04 will still be supported until 2017.

In terms of fixing it yourself, how comfortable are you with Python?

---

### Post by card06 on 2014-01-12
Well I'm not a Python expert that's for sure, but I do have a well knowledge of it. I have worked with it in professional environments as well and I think that with the right guidance about the Ubuntu system and how to properly modify it without crashing my whole system, then I think I could fix that. 
Regarding the filing of the report, I ran your command it sended the report, actually every time that my Software Center crashed, the same window popped up so I guess the bug filing was already sent some time ago.

Thanks for your help and if you could help me to fix the bug it would be even better :)

Kind regards

---


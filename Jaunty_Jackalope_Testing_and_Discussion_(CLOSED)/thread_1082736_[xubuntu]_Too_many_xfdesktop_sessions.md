---
title: "[xubuntu] Too many xfdesktop sessions?"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by useResa on 2009-02-28
I recently noticed quite a slowdown in startup between logging in and the moment the desktop is displayed. Furthermore memory usage seemed much higher than "normal".
When looking at the running sessions I noticed that I have a (very high) number of xfdesktop sessions running.
```
rdrijsen@xubuntu-pIII:~$ ps -ef | grep xfdesktop
rdrijsen  3604  3385  2 21:45 ?        00:00:07 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3607  3385  0 21:45 ?        00:00:01 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3615  3385  0 21:45 ?        00:00:01 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3617  3385 25 21:45 ?        00:01:04 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3619  3385  0 21:45 ?        00:00:01 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3622  3385  1 21:45 ?        00:00:02 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3625  3385  1 21:45 ?        00:00:03 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3631  3385  1 21:45 ?        00:00:05 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3632  3385  0 21:45 ?        00:00:01 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3637  3385  0 21:45 ?        00:00:01 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
rdrijsen  3640  3385  0 21:45 ?        00:00:01 xfdesktop --sm-client-id 20e707f1a-d6ed-463f-9e3b-8e911591050d --display :0.0
```What I would like to know:
* Is there a way that I can stop these sessions (killall xfdesktop?)
* How can I assure that at next startup only the appropriate number of sessions is started
I have two desktops so my assumption is that a maximum of two sessions should be running. Is this assumption correct?

BTW: As a comparison I looked at the number of xfdesktop sessions running in my Dreamlinux installation and there I found only 1

---

### Post by useResa on 2009-03-04
Finally had some time to dive into this issue.
Googling around I found that the started sessions are stored in the ~/.cache/sessions directory. Doing an ls of this directory I got the following result
```
Thunar-26260a357-5305-4d24-b334-02d6fcab9a31
Thunar-27973d142-7190-49e4-b2b9-23887e441e2d
Thunar-2e3ade537-14e3-4ee7-bd51-e7229f4b53ab
xfce4-session-xubuntu-pIII:0
xfce4-session-xubuntu-pIII:0.bak
xfwm4-20332b7cd-6ae3-49f1-b302-0e8418e66cd1
xfwm4-203696368-dfa8-47d3-a6ce-b19c63aa4a01
xfwm4-20484ae7c-36c1-41fd-8bd7-3b23678e2cbd
xfwm4-2478ffb37-e1e9-49c3-bf88-ffa147799403
xfwm4-249f7041d-7eb6-4459-b8d8-db16a3f1eea7
xfwm4-24aec6f86-9d96-4f84-8b78-3124a5ec9075
xfwm4-26570f867-2c1e-407f-99df-767f3c659d75
xfwm4-268fd2df1-5f4d-4046-8f16-862f096ca52b
xfwm4-27ab55dfe-3c74-402e-8af0-01f260adf5f1
xfwm4-281453ccf-74e3-40ca-815b-bb55229c8cf2
xfwm4-281f3c18e-4701-4c8f-869b-8264da73a93d
xfwm4-2859ca37a-8d51-468c-b777-aa55bab22f4d
xfwm4-2b835970a-a3f7-4061-8c9e-f820e3736e59
xfwm4-2c9c76039-be90-45d3-bfa6-51f294abde99
xfwm4-2e394e8c2-a17f-4264-99ef-c8a848c1fdfd
xfwm4-2e8ae97f7-462c-4aef-a73f-8fc5072834b3
xfwm4-2f0b8e1b8-5d63-4e6c-84e9-45b3f14dbbc4
xfwm4-2f4bc0dc0-13a9-4697-b251-1d1d9a38a909
xfwm4-2f639a019-43cb-458b-813f-b0850637a5ee
xfwm4-2f8a010d9-2ca5-4044-93b2-4ccddf01cabb
```

So I opened a terminal, cd-ed into the ~/.cache directory and issued (just to be safe) the following command
```
mv ./sessions ~/old_cache_sessions
```

Next I logged out and back in and ... the desktop appeared with a speed I was accustomed to before the issue. Performing a check I noticed that I only have one session now and that my ~/.cache/sessions has got a lot less entries.
```
rdrijsen@xubuntu-pIII:~$ ps -ef | grep xfdesktop
rdrijsen  6611     1  4 21:40 ?        00:00:01 xfdesktop
rdrijsen  6662  6645  0 21:41 pts/0    00:00:00 grep xfdesktop
rdrijsen@xubuntu-pIII:~$ ls ~/.cache/sessions
Thunar-2de1579c5-c0d7-42ba-8df1-75bbf7b174ee
```

So ... resolved  :D

---


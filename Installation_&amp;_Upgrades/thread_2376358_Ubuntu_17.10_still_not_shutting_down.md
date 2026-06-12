---
title: "Ubuntu 17.10 still not shutting down"
date: 2017-11-02
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2017-11-02
I did the Ubuntu 17.04 to 17.10 upgrade & have been working through many a kink ever since: the most problematic one at this point is that I still can't get my laptop to shut down properly. I've tried multiple shutdown commands through my terminal & it still doesn't work. I've seen lots of posts about Nvida cards, but I don't have one of those. Mine is an intel & when a I run the lspic | grep VGA command I get: 
```

Aspire-F5-571T:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
```

I'd really appreciate some help on this please. Its been over a week that this has been an issue & several other posts that I've made about this have either gone unanswered or the only suggestions given were using poweroff command in terminal & I doubt its a lack of terminal 'turn off' commands that is my challenge. Maybe Intel is having the same issue as the Nvidia? Any help would be greatly appreciated: thank you very much.

---

### Post by ynota on 2017-11-02
spencer2 when you try to shutdown using the terminal does your system hang? Do you get an error message on the command line? Have you checked your /var/log/syslog for errors? Have you tried to use the command > sudo shutdown -h now (that is assuming you have sudo setup). To get any help you will need to give some more information,"[COLOR=#000000]still can't get my laptop to shut down properly[/COLOR]" can mean a lot of things.

---

### Post by spencer2 on 2017-11-05
I used the shut down command you provide & on the shut down I get:

 INFO task kworker blocked for more than 120 seconds.
not tainted 4.13.0-16-generic #19-Ubuntu 
echo 0 > /proc/sys/kernel/hung_task_timeout_secs: disables this message. 


I looked that up & found a couple links, read them:

[URL="https://askubuntu.com/questions/965856/kworker-blocked-for-more-than-120-seconds-ubuntu-17-10"]https://askubuntu.com/questions/965856/kworker-blocked-for-more-than-120-seconds-ubuntu-17-10

[https://github.com/systemd/systemd/issues/2868](https://github.com/systemd/systemd/issues/2868)

https://www.blackmoreops.com/2014/09/22/linux-kernel-panic-issue-fix-hung_task_timeout_secs-blocked-120-seconds-problem/[/URL]
<
When I look at the syslog I do see this a lot:

```
wpa_supplicant [1289]: wlp3s0:CTRL-EVENT-SCAN-FAILED ret=-16 retry=1
```

Sorry for my lack of some of the basics & such: is there something specific in the syslog that I should look for? This isn't easily solved by going into kernel/hung_timeout file & just commenting out the 120? 

You're correct that my title needed to be worded better: I just  literally didn't know what to put. I'd seen a lot of stuff about the  video cards causing problems, your shutdown command was the first one  that gave me any sort of error data as all the other commands (reboot,  shutdown -c, poweroff, etc), never gave me any error codes. Thank you  for your help: its greatly appreciated.

---


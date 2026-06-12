---
title: "Postfix not sending mail through M365"
date: 2022-12-09
forum: Installation &amp; Upgrades
---

### Post by toddehb on 2022-12-09
Hi,

[COLOR=#232629][FONT=-apple-system]trying to setup my VPS with postfix and M365 as a relay host. Read several tutorials, but for some reason none of them does the job.Followed this instruction [/FONT][/COLOR][enter link description here]("https://blog.virtualcenter.com/2022/03/24/smtp-using-office-365-email-account-with-postfix-relay-on-ubuntu/")[COLOR=#232629][FONT=-apple-system], but postfix resp. M365 is throwing  error shown in the screenshots from attachment.

Weird thing is, that when I sent mail from another server to postfix, in this case a pfense box, the postfix is relaying correctly through M365 and the mail arrives in the inbox of that Gmail user.

For some reason M365 has a problem with the sender that is created from the console. It is [email]mailer-daemon@host.domain.com[/email]. In pfsense I can chose which sender address to use. Maybe I need to tell postfix to re-write all sender addresses which are generated within the system with  e.g [email]name@domain.com[/email] . How would that be realized or do you guys see another option? 

Cheers, todde


[/FONT][/COLOR]

---


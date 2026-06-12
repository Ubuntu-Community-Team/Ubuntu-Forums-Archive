---
title: "Oracle 10g - Can't start enterprise manager - Timezone c onflict?"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Invictus9 on 2007-03-18
Hey all,

I've been able to get Oracle 10gR2 installed on Ubuntu 6.10 - that is, everything except being able to get Enterprise Manager to be able to start.

- When I installed Ubuntu, I selected "America/Edmonton" as my time zone. I live in Alberta, Canada on Mountain time.
- When I run  "emctl start dbconsole", here's the error I get:

[FONT="Courier New"]Timezone mismatch: The agentTZRegion value (Canada/Mountain) in
 /u01/app/oracle/product/10.2.0/(host&dbname)/sysman/config/emd.properties
does not match the current environment TZ setting(Canada/Mountain).
The dbconsole cannot run with this mismatch.

If Canada/Mountain is the correct timezone, set your timezone environment variable to Canada/Mountain and repeat the 'emctl start dbconsole' operation.

If Canada/Mountain is not the correct timezone, make sure that the timezone in your environment is correct, and then run the following command in your local Oracle Home: 'emctl resetTZ agent'

The output of this command will include detailed instructions to follow, to correct the mismatch.

[/FONT]

- I've edited the /etc/timezone file and typed in Canada/Mountain. I still get this error.
- I've set an environment variable for "TZ=Canada/Mountain". Still no luck.

What am I missing???? Please help, I'm trying to practice for my certification exam, and I really need to get this working, even though I know it's not officially supported on Ubuntu. But I'm sure someone knows a workaround for this.

Ken

---

### Post by Invictus9 on 2007-03-19
Anyone??

---

### Post by mcmanus on 2008-03-14
I have this same problem, although I don't know if it makes a difference that I'm running Ubuntu 7.10 Server in Parallels.  I have my /etc/localtime linked to CST6CDT and /etc/timezone shows America/Chicago.  NTP is running and is setting the date correctly too (and system clock is not set to UTC).

---

### Post by p2000000000 on 2008-06-19
have you tried running this?
```
emctl resetTZ agent
```

---


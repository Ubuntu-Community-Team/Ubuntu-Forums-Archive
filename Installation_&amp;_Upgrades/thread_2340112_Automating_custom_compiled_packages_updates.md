---
title: "Automating custom compiled packages updates"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by carnaval on 2016-10-15
I read that apt-get can download source packages from source repositories. And that got me wondering if it would be possible to automate custom builds so that every time a package is updated in a repository, the new version can be automatically compiled with the same config options.

If that is something that people already do, can you please point me to how to do it? If not, what are other options that can accomplish the same or similar results?

Thank you in advance.

---

### Post by TheFu on 2016-10-18
We use ansible and don't cross-contaminate those source installed programs with APT installed programs.

---

### Post by carnaval on 2016-10-18
Thank you for responding.

I was hoping for a way to accomplish this task without adding more packages to the system. But will look into ansible.

---

### Post by TheFu on 2016-10-18
You can script whatever you like using whatever language you prefer. Ansible is just a standard way of managing systems. Nothing more. Nothing less.

Ansible is only needed for 1 system, the workstation used to launch the management of 2-20,000 other systems.

---

### Post by carnaval on 2016-10-19
That should make things easy. Will try it out in my test environment. Thank you again.

---


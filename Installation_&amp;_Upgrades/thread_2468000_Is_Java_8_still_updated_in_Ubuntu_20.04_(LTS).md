---
title: "Is Java 8 still updated in Ubuntu 20.04 (LTS)?"
date: 2021-10-15
forum: Installation &amp; Upgrades
---

### Post by realst37 on 2021-10-15
Hello,

I was wondering why Java 8 (openjdk-8-jdk) on my Ubuntu 20.04 (LTS) machine still is at version **8u292** and doesn't find any newer version via "apt update". The latest version of OpenJDK 8, at the time of this writing, is **8u302**, released on July 20th 2021:
[https://wiki.openjdk.java.net/display/jdk8u/Main](https://wiki.openjdk.java.net/display/jdk8u/Main)

For example, *Adoptium.net* and *Liberica JDK* are offering Linux builds of OpenJDK version **8u302** for a long time now!

Since Ubuntu 20.04 (LTS) is supposed to get "free" updates until **Apr 2025**, why is it that the included Java 8 (openjdk-8-jdk) packages, apprently, do ***not*** receive updates anymore at this point in time? :neutral:

I understand that existing releases of Ubuntu won't incoporate new "major" versions of Java, such as Java 17 (LTS).

But shouldn't at least those "major" versions of Java, that ***are* **included in Ubuntu 20.04 (LTS), be kept *up-to-date *with to the _latest_ OpenJDK "patch" version, for as long as Ubuntu 20.04 (LTS) is still in "standard support" phase :?:

After all, new "patch" versions of OpenJDK 8 may contain bugfixes or even fix some security vulnerabilities...

Thank you!

---

### Post by pcfan1234 on 2021-10-16
It is in universe, so not maintained by Canonical.
Maybe file a bug so the MOTU team can update it.

---

### Post by spattent on 2021-10-18
> **pcfan1234 said:**
> It is in universe, so not maintained by Canonical.

Can you please eloberate on that? I'm using Ubuntu 20.04 LTS with only "standard" out-of-the-box package repositories. No PPA or the like hase been added.

To my understanding, these "official" Ubuntu package repositories - even though being based on Debian Linux - are maintained by the Ubuntu developers (Canonical), aren't they?

So, Java 8 (openjdk-8-jdk) was installed from "official" Ubuntu package repositories and should be updated to the latest OpenJDK 8 "patch" version *there*, I think.

> **pcfan1234 said:**
> Maybe file a bug so the MOTU team can update it.

Sorry, it may be obviosus for most users here, but I have no idea what MOTU is :confused:

Google brings up "*Mark of the Unicorn (MOTU) is a music-related computer software and hardware supplier*". But how are they involved with Ubuntu and especially its Java/OpenJDK packages?

Thank you.

---

### Post by Impavidus on 2021-10-18
See [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

There are 4 sections in the repositories: main, restricted, universe, multiverse. They differ in terms of support and licensing.

---

### Post by coffeecat on 2021-10-18
> **spattent said:**
> Google brings up "*Mark of the Unicorn (MOTU) is a music-related computer software and hardware supplier*". But how are they involved with Ubuntu and especially its Java/OpenJDK packages?


They aren't. Presumably you merely googled "motu". If you google "Ubuntu motu", then the first hit is this:

[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by spattent on 2021-10-18
> **coffeecat said:**
> They aren't. Presumably you merely googled "motu". If you google "Ubuntu motu", then the first hit is this:

[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

I see. Thanks for the pointer!

So, if I get this right, the OpenJDK 8 package is provided from a separate repository called "universe". And the software in that repository is maintained by contributors known as "MOTU" rather than Canonical themselves.

I wasn't aware of that. But I'm still not quite sure what to do. The Wiki page has some info on how to become a MOTU, but that is ***way*** beyond my scope :redface:

I really just wanted to understand why the "openjdk-8-jdk" package in Ubuntu 20.04 LTS is **no** longer kept *up-to-date* with the latest "patch" version of [Open JDK 8]("https://wiki.openjdk.java.net/display/jdk8u/Main"), even though Ubuntu 20.04 LTS is still supported until **Apr 2025**.

Am I correct to assume that this is simply because non of the MUTO members has stepped up and uploaded the new version into "universe"?

For "normal" users like me, would this mean that we can **not** expect _reliable_ updates for any packages that come from "universe"? That would actually be quite *unfortunate* for an LTS release, where you'd hope to get at least security updates and bugfixes _in a realibly way_ for a long time... :o

Should I switch to Open JDK 8 packages from [Liberica JDK]("https://bell-sw.com/pages/repositories/#apt") instead?

Regards.

---

### Post by pcfan1234 on 2021-10-18
>  I really just wanted to understand why the "openjdk-8-jdk" package in Ubuntu 20.04 LTS is **no** longer kept *up-to-date* with the latest "patch" version of [Open JDK 8]("https://wiki.openjdk.java.net/display/jdk8u/Main"), even though Ubuntu 20.04 LTS is still supported until **Apr 2025**.
The official support end Apr 2025 only applies to packages coming from main and restricted. The support end for universe differs from package to package.
I recommend filing a bug in Launchpad for OpenJDK8, so the maintainers can provide an update.

---

### Post by spattent on 2021-10-18
> **pcfan1234 said:**
> The official support end Apr 2025 only applies to packages coming from main and restricted. The support end for universe differs from package to package.
Is there any place where I can see the EOL date for each package in universe?

> **pcfan1234 said:**
> I recommend filing a bug in Launchpad for OpenJDK8, so the maintainers can provide an update.
Thanks for the pointer. Did that.

---

### Post by pcfan1234 on 2021-10-18
> **spattent said:**
> Is there any place where I can see the EOL date for each package in universe?

Sorry, I don't know any.

---

### Post by monkeybrain20122 on 2021-10-19
> **spattent said:**
> 
Should I switch to Open JDK 8 packages from [Liberica JDK]("https://bell-sw.com/pages/repositories/#apt") instead?



Just keep Liberica

---


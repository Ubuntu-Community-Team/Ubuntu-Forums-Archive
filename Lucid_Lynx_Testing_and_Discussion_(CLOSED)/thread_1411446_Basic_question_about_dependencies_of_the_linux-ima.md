---
title: "Basic question about dependencies of the linux-image-...-generic packages"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by benblout on 2010-02-19
When I examine packages using synaptic, I see I have
linux-image-generic version 2.6.32.13.14 installed, which depends on
the package linux-image-2.6.8.32-13-generic.  This seems odd given the
version number and names.

In addition, my system has installed linux-image-2.6.32.13-generic,
while I am showing as being available linux-image-2.6.32-14-generic.
And linux-image-2.6.32-14-generic has no dependants.  Is there a
dependency mistake somewhere, or am I confused about how things are
supposed to work?

---

### Post by jocko on 2010-02-20
> **benblout said:**
> When I examine packages using synaptic, I see I have
linux-image-generic version 2.6.32.13.14 installed, which depends on
the package linux-image-2.6.8.32-13-generic.  This seems odd given the
version number and names.

How is that odd? The package linux-image-generic is a meta package that is only there to make sure you have the latest generic kernel image installed. It does not have to have the same version number as the actual kernel image package. The meta package is now 2.6.32-**13.14**, and it depends on the package linux-image-2.6.32.13-generic (which now has the version 2.6.32-**13.18**). The dependency is only for the name of the package and not the actual version number.

> **benblout said:**
> In addition, my system has installed linux-image-2.6.32.13-generic,
while I am showing as being available linux-image-2.6.32-14-generic.
And linux-image-2.6.32-14-generic has no dependants.  Is there a
dependency mistake somewhere, or am I confused about how things are
supposed to work?The fact that the repos contain a newer kernel than the one you are using simply means that the meta package which would lead to installing the new kernel is not available yet. There are reasons for this, perhaps some of the other packages that needs to be updated at the same time are not ready yet. When everything else is ready for it, the package linux-image-generic will be updated to one that depends on linux-image-2.6.32-14-generic.
Remember you are using an alpha version. That means updates enter the repos all the time, so the dependency chains for all packages can not always be in sync. So relax. there is nothing wrong.

---

### Post by benblout on 2010-02-20
> **jocko said:**
> How is that odd? <snip> The meta package is now 2.6.32-**13.14**, and it depends on the package linux-image-2.6.32.13-generic (which now has the version 2.6.32-**13.18**). The dependency is only for the name of the package and not the actual version number.

Ah, I see my mistake.

> **jocko said:**
> The fact that the repos contain a newer kernel than the one you are using simply means that the meta package which would lead to installing the new kernel is not available yet.<snip>

<snip>...updates enter the repos all the time, so the dependency chains for all packages can not always be in sync. So relax. there is nothing wrong.

OK, I see what is going on.  I was suffering partially from misunderstanding the numbering system, and partially from being confused.  Thank you for straighting me out.  

(And I was relaxed. :-)  Confused, but relaxed.)

---

### Post by jocko on 2010-02-20
> **benblout said:**
> Thank you for straighting me out.
You're welcome.

---


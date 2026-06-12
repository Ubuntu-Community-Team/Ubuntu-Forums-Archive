---
title: "Could not download the upgrades"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by BradleyAtkins on 2012-08-20
Hi 

I could do with a few pointers as to how to investigate this issue. 

I am being offered "Partial Upgrades" with a message that the problem is probably caused by a third party install.

When I accept the partial install I get this error -

```
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.9-1ubuntu2.2_i386.deb 404  Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4_4.8.9-1ubuntu2.2_i386.deb 404  Not Found

```

The URL doesn't seem to exist and I don't know why the update manager is looking for them.

Are their some logs associated with this kind of error that I could examine to find out what is expecting these downloads?

Hopefully it is just some app I can remove.

Thanks

Brad

---

### Post by yatot on 2012-08-20
i got the same error too by this time. what seems to be the hold-up for the upgrades?

---

### Post by westie457 on 2012-08-20
> **BradleyAtkins said:**
> Hi 

I could do with a few pointers as to how to investigate this issue. 

I am being offered "Partial Upgrades" with a message that the problem is probably caused by a third party install.

When I accept the partial install I get this error -

```
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.9-1ubuntu2.2_i386.deb 404  Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4_4.8.9-1ubuntu2.2_i386.deb 404  Not Found

```

The URL doesn't seem to exist and I don't know why the update manager is looking for them.

Are their some logs associated with this kind of error that I could examine to find out what is expecting these downloads?

Hopefully it is just some app I can remove.

Thanks

Brad

Hi, no idea what update manager is looking for so a work around for you.

Open 'Software Sources' find those entries causing the errors and un-check them. Close out of 'Software Sources'. Then open a terminal and run ```
sudo apt-get update

sudo apt-get upgrade
```

Report back here if any more errors.

Thank you

---


---
title: "apt update: signatures couldn't be verified because the public key is not available"
date: 2020-03-17
forum: Installation &amp; Upgrades
---

### Post by 7eieio on 2020-03-17
When running the command:

```
sudo apt update
```

I get the following error:

    ```
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ACFA9FC57E6C5DBE
```

After checking about 10 references regarding the same issue, the "fix" is always the same:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ACFA9FC57E6C5DBE
```

And the output:

```
Executing: /tmp/apt-key-gpghome.sIK5cNh7ta/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys ACFA9FC57E6C5DBE
gpg: key ACFA9FC57E6C5DBE: "Intel(R) Software Development Products" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

However after trying to add the key I continue to get the same error running update.  The output of the apt-key command seems to indicate nothing was changed.

Unfortunately I have not found someone else out there for which it also does not work after adding the key, and I've found nothing else on the suibject.

Help?!?

Thanks kindly....

---

### Post by logix2 on 2020-03-18
It looks like the key has expired, and you need to install the new key. According to [this]("https://software.intel.com/en-us/forums/intel-math-kernel-library/topic/821365"), you need to reinstall the key by following the instructions from [https://software.intel.com/en-us/articles/installing-intel-free-libs-and-python-apt-repo](https://software.intel.com/en-us/articles/installing-intel-free-libs-and-python-apt-repo)

---

### Post by 7eieio on 2020-03-23
> **logix2 said:**
> It looks like the key has expired, and you need to install the new key. According to [this]("https://software.intel.com/en-us/forums/intel-math-kernel-library/topic/821365"), you need to reinstall the key by following the instructions from [https://software.intel.com/en-us/articles/installing-intel-free-libs-and-python-apt-repo](https://software.intel.com/en-us/articles/installing-intel-free-libs-and-python-apt-repo)

Thanks, that worked.  Not sure why I have both add the key if I am installing the repos manually, but nevertheless it worked anyway.

BTW, sorry for the late reply, my account appears to be screwed up (My screen name is NOT 7eieio) and I haven't been getting notices.

---

### Post by 7eieio on 2020-03-23
Arrrrrgggg... Well it looked like it was working.  I got past my error but at the end of `sudo apt-get update` I get this:

W: Conflicting distribution: [https://apt.repos.intel.com/intelpython](https://apt.repos.intel.com/intelpython) binary/ InRelease (expected binary/ but got )

Hoping it would be something I could ignore for now, I tried installing my package, but got errors.  So I thought I would try updating Ubuntu using the package manager:

```
update-manager -c
```

App opens, starts downloading packages, then aborts when it can't get apt.repos.intel.com/intelpython.  So I do
`curl [https://apt.repos.intel.com/intelpython](https://apt.repos.intel.com/intelpython)`

and get

```
<?xml version="1.0" encoding="UTF-8"?>
<Error><Code>AccessDenied</Code><Message>Access Denied</Message><RequestId>490F1A3B2AB20E36</RequestId>
<HostId>I6D3QdC0n2iRZdoOC/aCMjW++FTlpyWaWPhfk3Iz1+cUfCD2c/C+CMv88pVebJuH7U1SSIqy3iM=</HostId></Error>
```

So I seem stuck, I can't even update my install :-/

---

### Post by 7eieio on 2020-03-23
Update, my system time was off, so this may be due to that.  Can't check right now but will report back when I can.

---

### Post by 7eieio on 2020-03-23
Yep, setting my system clock fixed the system update thing.

Thanks for the help

---


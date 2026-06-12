---
title: "apt update not able to get the Release file from a redirect URL"
date: 2018-02-22
forum: Installation &amp; Upgrades
---

### Post by nwei on 2018-02-22
Hi! We have been hosting our own Debian repository for some time now. When `apt` was recently upgraded to `v1.2.25`, `apt update` is no longer able to find the `Release` file in our deb repo. We get the following ignore messages:

```

Ign:6 http://packages.cloudfoundry.org/debian stable Release
Ign:8 http://packages.cloudfoundry.org/debian stable/main all Packages

```

we expect to get (which we see on apt v1.2.15, v1.2.24, and v1.5.x):

```
Get:6 https://cf-cli-debian-repo.s3.amazonaws.com stable Release [1797 B]
Get:7 https://cf-cli-debian-repo.s3.amazonaws.com stable Release.gpg [819 B]

```

The URLs above are redirects to where these assets actually live.

We verified that:
1. where we host these static assets are working as expected
2. our redirect app is working as expected

When we used other[COLOR=#000000] versions of `apt` (v[/COLOR][FONT=Ubuntu][[COLOR=#000000]1.2.15ubuntu0.2[/COLOR]]("https://launchpad.net/ubuntu/+source/apt/1.2.15ubuntu0.2")[COLOR=#000000], [/COLOR][/FONT][COLOR=#000000], v1.2.24, and v1.5.x), the `apt update` works and is able to get the contents of the Release file.

We have a support ticket open for this which includes reproduction steps: [/COLOR][https://github.com/cloudfoundry/cli/issues/1327](https://github.com/cloudfoundry/cli/issues/1327)

---

### Post by QIII on 2018-02-22
Is this an issue related to using xenial-updates in Ubuntu?

---

### Post by nwei on 2018-02-22
We discovered additional data points on this issue. It turns out when we register our Debian repo in the `[COLOR=#24292E][FONT=SFMono-Regular]/etc/apt/sources.list.d[/FONT][/COLOR]` directory, we provide a `http` URL instead of `https`. After switching to the `https` protocol for the same URL, `apt update` works as expected to get the `Release` and `Release.gpg` files. Is this change in behavior mentioned in the apt v1.2.25 release notes?

---

### Post by QIII on 2018-02-22
Again:  Ubuntu release notes?

---

### Post by nwei on 2018-02-23
Thanks for pointing that out. This is not related to the ubuntu xenial release notes. This is specific to apt release notes. Am I in the wrong forum channel? Could you please point me in the right direction? Thanks.

---


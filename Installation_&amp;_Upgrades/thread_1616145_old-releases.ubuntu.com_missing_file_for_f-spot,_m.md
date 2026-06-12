---
title: "old-releases.ubuntu.com missing file for f-spot, mono"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by cocooner on 2010-11-07
I'm getting a file not found error when trying to install f-spot, mono.

```

&#50724;&#47448; http://old-releases.ubuntu.com intrepid-updates/main f-spot 0.5.0.3-0ubuntu4
  404 Not Found
&#50724;&#47448; http://old-releases.ubuntu.com intrepid-updates/main sqlite3 3.5.9-3ubuntu1
  404 Not Found
&#50724;&#47448; http://old-releases.ubuntu.com intrepid-updates/main mono-common 1.9.1+dfsg-4ubuntu2.1
  404 Not Found
&#50724;&#47448; http://old-releases.ubuntu.com intrepid-updates/main mono-jit 1.9.1+dfsg-4ubuntu2.1
  404 Not Found
&#50724;&#47448; http://old-releases.ubuntu.com intrepid-updates/main mono-runtime 1.9.1+dfsg-4ubuntu2.1
  404 Not Found
&#50724;&#47448; http://old-releases.ubuntu.com intrepid-updates/main libmono0 1.9.1+dfsg-4ubuntu2.1
  404 Not Found
http://old-releases.ubuntu.com/ubuntu/pool/main/m/mono/mono-common_1.9.1+dfsg-4ubuntu2.1_i386.deb &#54028;&#51068;&#51012; &#48155;&#45716; &#45936; &#49892;&#54056;&#54664;&#49845;&#45768;&#45796;  404 Not Found
http://old-releases.ubuntu.com/ubuntu/pool/main/m/mono/mono-jit_1.9.1+dfsg-4ubuntu2.1_i386.deb &#54028;&#51068;&#51012; &#48155;&#45716; &#45936; &#49892;&#54056;&#54664;&#49845;&#45768;&#45796;  404 Not Found
http://old-releases.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_1.9.1+dfsg-4ubuntu2.1_i386.deb &#54028;&#51068;&#51012; &#48155;&#45716; &#45936; &#49892;&#54056;&#54664;&#49845;&#45768;&#45796;  404 Not Found
http://old-releases.ubuntu.com/ubuntu/pool/main/m/mono/libmono0_1.9.1+dfsg-4ubuntu2.1_i386.deb &#54028;&#51068;&#51012; &#48155;&#45716; &#45936; &#49892;&#54056;&#54664;&#49845;&#45768;&#45796;  404 Not Found
http://old-releases.ubuntu.com/ubuntu/pool/main/f/f-spot/f-spot_0.5.0.3-0ubuntu4_i386.deb &#54028;&#51068;&#51012; &#48155;&#45716; &#45936; &#49892;&#54056;&#54664;&#49845;&#45768;&#45796;  404 Not Found
http://old-releases.ubuntu.com/ubuntu/pool/main/s/sqlite3/sqlite3_3.5.9-3ubuntu1_i386.deb &#54028;&#51068;&#51012; &#48155;&#45716; &#45936; &#49892;&#54056;&#54664;&#49845;&#45768;&#45796;  404 Not Found
E: &#50500;&#52852;&#51060;&#48652;&#47484; &#48155;&#51012; &#49688; &#50630;&#49845;&#45768;&#45796;. &#50500;&#47560;&#46020; apt-get update&#47484; &#49892;&#54665;&#54644;&#50556; &#54616;&#44144;&#45208; --fix-missing &#50741;&#49496;&#51012; &#51480;&#49436; &#49892;&#54665;&#54644;&#50556; &#54624; &#44163;&#51077;&#45768;&#45796;.

```sources.list

```

# Ubuntu Repository
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe

```How to solve this problem?

---

### Post by directhex on 2010-11-08
Looks like the i386 and amd64 packages for it are missing.

Try filing a bug against Launchpad.

---


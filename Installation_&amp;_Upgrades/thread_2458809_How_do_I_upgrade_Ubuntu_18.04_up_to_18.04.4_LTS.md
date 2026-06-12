---
title: "How do I upgrade Ubuntu 18.04 up to 18.04.4 LTS?"
date: 2021-03-04
forum: Installation &amp; Upgrades
---

### Post by goahead97 on 2021-03-04
Hello

I want to install 64 bits Ubuntu 18.04.4 LTS in an external SSD for a 64 bits computer. I already downloaded and installed the desktop Ubuntu downloadable from the following link:
[http://old-releases.ubuntu.com/releases/18.04.4/](http://old-releases.ubuntu.com/releases/18.04.4/) Nonetheless, for some strange reason, if I type [HTML]lsb_release -a[/HTML] I see 18.04 instead of 18.04.4. That means, even I though I ended up downloading and installing the desktop Ubuntu image of the mentioned link, the minor version that got installed is 18.04.

Moreover, I think the most up-to-date minor version of Ubuntu 18.04 is 18.04.5 LTS. Considering I need to install Ubuntu 18.04.4, what commands should I type in command terminal in order to get my operating system upgraded, making sure that it gets upgraded only up to the minor version 18.04.4 LTS, instead of up to the most up-to-date minor version, that means 18.04.5 LTS?

Thanks

---

### Post by ubfan1 on 2021-03-04
The point releases after the initial 18.04.1  just differ by the kernel they offer.  You can keep the original kernel for the support life of the release if you want by installing the 18.04.1 , or get more recent kernels starting with .2 but only with a 9 month support life.  You can always add the hwe packages for later kernels any time you want.

---

### Post by CatKiller on 2021-03-04
The point releases are simply an updated image of the then-current software, so that you have less to download at install time. Whether you install the earliest iso and then update, or install the latest iso and then update, you'll be running exactly the same software. For 16.04 and 18.04 the .2 release enabled the HWE stack by default, whereas the .0 and .1 releases didn't, but from 20.04 onwards the HWE stack is enabled by default, where appropriate, on all releases. 18.04.4 isn't a version, it's simply a release; the version is 18.04 LTS.

---

### Post by Impavidus on 2021-03-04
The point release only matter for the live disk images. If lsb_release -a gives some number, that doesn't mean much. I'm not sure it actually gives a number, as I'm on an interim release, so no point release number anyway. If you installed from the 18.04.4 image, you should have 18.04 more or less in the state with all updates released until 1-2020. The differences between 18.04.4 and 18.04.5 are a newer version of Firefox, a kernel from the 5.4 series instead of 5.3 (I think) and some bugfixes. The older kernel series (from Ubuntu 19.10) is no longer supported, so don't use it.

---

### Post by goahead97 on 2021-03-04
For example, I installed LXLE 64 bits Ubuntu 18.04.3 on another external SSD and I upgraded to the last minor and now lsb_release outputs the following:

```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:        18.04
Codename:       bionic

```

I thought I could do something like this in order to upgrade the Ubuntu 18.04 I  got from
[http://old-releases.ubuntu.com/releases/18.04.4/](http://old-releases.ubuntu.com/releases/18.04.4/)[COLOR=#000000] 
up to Ubuntu 18.04.4.

When I boot with the external SSD where I installed the desktop Ubuntu image of [/COLOR][http://old-releases.ubuntu.com/releases/18.04.4/](http://old-releases.ubuntu.com/releases/18.04.4/)
[COLOR=#000000]the command lsb_release -a outputs the following:

[/COLOR]```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04 LTS
Release:        18.04
Codename:       bionic
```[COLOR=#000000]
Considering I see 18.04.4 LTS nowhere in the output of > lsb_release -a, I wonder what must be done to upgrade to Ubuntu 18.04.4 LTS.

Even though I could just upgrade to the most up-to-date minor release (Ubuntu 18.04.5) of Ubuntu 18.04, I need to use Vitis 2020.2 and as far as I read on 
[/COLOR]https://www.xilinx.com/html_docs/xilinx2020_2/vitis_doc/acceleration_installation.html#vhc1571429852245
among minor releases of Ubuntu 18.04, only 18.04.1, 18.04.2, 18.04.3 and 18.04.4 are, according to the explicit mention of the aforementioned link, compatible with Vitis 2020.2.

This is the reason why I would like to know how I could get Ubuntu 18.04.4 and how to be sure I exactly got that version and nothing beyond that.

By the way, even though Ubuntu 20.4 seems to be compatible as well with Vitis 2020.2 according to that link, I also need to use a hardware device that is only compatible with releases of Ubuntu 16.04 or 18.04.

Thanks

---

### Post by grahammechanical on 2021-03-04
With

```
lsb_release -a
```

We do get a point number. As on my install.

> Graham@sdb1-sdb8:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal


What does the description say?

Regards

P.S. The command simply prints in the terminal the contents of the text file /etc/lsb-release. There is no trickery here.

---

### Post by goahead97 on 2021-03-04
[COLOR=#000000][COLOR=#000000]When I boot with the external SSD where I installed the desktop Ubuntu image of [/COLOR][/COLOR][http://old-releases.ubuntu.com/releases/18.04.4/](http://old-releases.ubuntu.com/releases/18.04.4/)
[COLOR=#000000][COLOR=#000000]the command lsb_release -a outputs the following:

[/COLOR][/COLOR][COLOR=#000000]```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04 LTS
Release:        18.04
Codename:       bionic

```

[/COLOR]Therefore the description says Ubuntu 18.04 LTS.

Are 18.04 and 18.04.1 synomyms?

Otherwise, what do I need to do to upgrade from 18.04 to one of the following?
18.04.1, 18.04.2, 18.04.3, 18.04.4

Thanks in advance.

---

### Post by deadflowr on 2021-03-04
> Are 18.04 and 18.04.1 synomyms?

No.
The difference between these two is the .1 point release contains all accumulated updates since the initial 18.04 release.
This is why it is recommended for productivity machines to hold off upgrading until the first point release is out.
Since the point release will have fixes applied that couldn't be fixed in the initial release. (either because not enough time, or because the issues weren't widely known)
Succeeding point releases apply the same updates process (applies all accumulated updates since the last point release)  
with the added bonus of moving up hardware stacks based on what the stacks of current standard (non-lts) releases are.

> Otherwise, what do I need to do to upgrade from 18.04 to one of the following?
Not possible anymore.
All updates will move directly to 18.04.5.

---

### Post by TheFu on 2021-03-04
Run:
```
sudo apt-get update
sudo apt-get full-upgrade
```

That should bump up the system to 18.04.5

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:        18.04
Codename:       bionic
```

Then you can install the HWE stuff. How depends on which DE you have installed.  There are instructions if you goolge "HWE Ubuntu" and look for your specific release.  That will get you to the 5.4.x kernel and update the X/Windows stuff.  5.4.x is the kernel on the normal 20.04 release. This can make newer hardware work better, but some older hardware may work less good too. Just depends. It is a risk.

BTW, it would have helped if you simply posted the **lsb_release -a** AND the output, so the posts above didn't have to interpret what you wrote and hope they did that correctly. I know I couldn't.

---

### Post by CatKiller on 2021-03-04
> **goahead97 said:**
> I wonder what must be done to upgrade to Ubuntu 18.04.4 LTS.

There is no such animal. Just stop. Install whatever release of 18.04 (or 20.04) that you have to hand, and run all your updates. You're running a fool's errand (and this isn't the first thread on the subject, IIRC) because they haven't got round to listing all the point releases on one page of their website. Contact your vendor to get them to update their documentation if you can be bothered.

---

### Post by grahammechanical on 2021-03-05
Download and install ubuntu-18.0.4-desktop-amd64.iso. And you will have Ubuntu 18.04.4 and I am certain that the lsb-release text file will say the installation is both 18.04 and 18.04.4. Be careful when you update/upgrade as that will upgrade 18.04.4 to 18.04.5. The only way I can think to keep 18.04.4 secure without it becoming 18.04.5 is to identify all the security patches to be installed and only allow Ubuntu Updates to install those packages. That is one year's worth of security fixes.

Regards

---

### Post by goahead97 on 2021-03-05
> **grahammechanical said:**
> Download and install ubuntu-18.0.4-desktop-amd64.iso. And you will have Ubuntu 18.04.4 and I am certain that the lsb-release text file will say the installation is both 18.04 and 18.04.4. Be careful when you update/upgrade as that will upgrade 18.04.4 to 18.04.5. The only way I can think to keep 18.04.4 secure without it becoming 18.04.5 is to identify all the security patches to be installed and only allow Ubuntu Updates to install those packages. That is one year's worth of security fixes.

Regards
Thanks a lot Graham.

I had downloaded the file from the link displayed in attachment as "default link.jpg" of [http://old-releases.ubuntu.com/releases/18.04.4/](http://old-releases.ubuntu.com/releases/18.04.4/)
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMoAAAAuCAYAAABpsIY8AAAF UlEQVR4Ae2aXXIcNwyE9zo Tw6Tkzt5lAup lytFkBilNWK68XDFH660SApYsZJ7e3ff36 zTNnMHdgfQduc0DrA5rzmfOJOzCDMl/U RdF4w7MoDQOab4q81WZQZlBmS9K4w7MoDQOab4o80WZQZlBmS9K4w7MoDQOab4o80X5PSi32 2tev7732O320PfPLGW0y7oiWu69xnpHtVf9VnxVthK8zTs96DowrLNZTmtGf/Pe t2/ Yr3gp7pjtzeVBi49nmyTtGjI3Dqbh6cMrv1qx46NFbe63qlIcGfKznNaaevisMPWqIqdW8 3BUX320qMv4GQc GHWeVzzDyFG/Whvck ylQdHNVX5szjGP9QAUq/LO8Zg6z2scvsedOjhhvX4XU6u8TEd5ylXf66jJ8tRh4RJjPe9aylM/4yne8V2DtZxqLw2KbqI6DD8A5TmWxfTQOvXBM s8jdX3vitM yhPfdfL4s/o7Hqopvpah49VHr5ilQ8Xu JVmOZDx2O0T7R3G5TYtD5s1g9DOfhw1a7qlKd VgO w1gLljq1qqF cDox2spV33WUj6/rUR8cCxax6xLDhUPeazXe1aw0tBYf7dPt3Qal2qj EfwQq5odzzXR8bzG6ru Y i5VZ76rufxinsF8/UQdzSUo/5qrcpTf1WzwlyD9T D/ZJB0QNR3w8xizk0rVO/W O8lcYKYz1X9Fbc6KX93Pe46l/lXd/X4rHzq/6e38Wsz3nkfR2aP9G/y6Cw6TgUPRjyvnF4zlWeY50a sHd6Tme1TmHOFsfWNgMJ4eFHzE5rGOeB8fuNOBhK772UT/qdjWKax981ci0lXeanw7KaYt8pfX4BXqlvZ 81xmUb/4JC29h7MmX5ZXXNoPyzYPyypfvmfY gzKDctxv6k4coBmUGZQZlMYdmEFpHNKJb7hZ02N/hDqDMoMyX5TGHZhBaRzSvL0f /Y 8bxnUGZQ5ovSuAMzKI1DOvENN2t67FduBmUGZb4ojTswg9I4pHl7P/btfeJ5z6DMoMwXpXEHZlAah3TiG27W9Niv3AzKDMp8URp34MOg/P3jrzee6q0VeIVFfoUrpr7qRd4fxfGVQ25lvZ/HUZvlPK998bO YJVmppvpVLmVblXj Uqjynt9N763XrfvvXjvBsU343E0jVyW1wXtcLgVL8t7bhfTA1vxs/wu53j08NwupqbDYw9uvdbxTlxpVPmO5p/IWQ5KtuE4wN0hgmdcx4i11y6X4VFf5TMMLpb Ee9yjmtt5pNzW/VynsZa4 sA83zUV5hzlaeY5n09qq Y q6V1dBD65SnGnC0xnEwz1N7xaaDQgMXoiHWcWKvV37lUxtWOeQ1pz74ymZ8cljqiSsbPDBqsJrHD4sPTzVWmPK1Bl9r1Qenvospr/Iz7RU3W0PwvcbjrC7rrbxKw uouWI/DEqnmXKyZo5rXPmqExx/HNd452vP4K5isMpm9fSnBo7H8MDVZpjmMm5HP6tTXTSwYBqr73orDK2rNa75GR3X8Fg1O/6HQdEiFV/5gVV46FWY5qu msev6sDdOj9if6iBW9nggVGD1bz6XqOY pkOOdfwOHT88Vrwbh6er1Fj9X1N1Ht V5PhkeNBN MpBh8L9hl7aVBoiK0aBq6YxpVf8TWPrxrkwnbzztMYv7LdPtSzPo3D9wdeV995qq9ama/cq/6ur ppb82r73oer7hXMF3LZ/z2oKi4L1Cx8ANXTsdXDeVrXn3neFxxKx55bNR3fPoo12uzuKq7wtWe6rtGF1Ne5WfaK262T W7nsfKDd9j1a8w16Tmin03KAj6glxQF QYGljnalz1UU6mT476Dh8OFg0seWzkV35g qCjdod7jyxWPfBKt8p7nWpGTRajBUbc5VOH1Tr1A /EcLCqSw7rmOfBr9gPg3Kl Jm49zisR z3WdbJWZy03q9cy8sMSvxhv/IguTj/x56 vmxv37nm6K1Ptr575V5qUO51aKPz2B8knnDeMyiNH8Sd8IeaNXzvcM6gzKC8 4/5Gch8IH8B/LQUfL qrFIAAAAASUVORK5CYII=[/IMG]

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAUIAAAAoCAYAAACLtfMUAAAGSElEQVR4Ae2bXY7jRgyEfZ2cJ4fJyZM8zoIBPqBSIFttj 3VWPUg8KeKxZZMcbUL7O3ff/7 ypVnkBnIDFx5Bm5Xvvnce17 zEBmoGYgizBfxPkbQWbg8jOQRZiX4PIvQb4K81WYRZhFmEWYGbj8DLSL8Ha7fU3Xf3 fvt3e uDqLGf7U/uMZ3r2M9J7VH/VZ8VbYSvNYPlie/UMtItQm3bD2 W0Jv7nDe7ub77irbDMzOfNzE/6Tb 1CGuwu Em7xgxth7UxNWHqPzdmhUPPXprr1Wd8tCAj/W8xtTTd4WhRw0xtZp3H47qq48WdR2/48AHo87zincYOepXZ4Mbm0X5yhl4eBHq8E5 Hdwxj/XmFJvyzvGYOs9rXL7HO3Vwynr9UUyt8jod5SlXfa jpstTh4VLjPW8aylP/Y6n I7vGpwlNsvvXTPw8CLUA07DXpxdzLm7 spTX/u69qPYpL/S896q4dhKZ4W5psZah49VHr5ikw8Xu JNmOZLx2O0Y7MM3zEDL1mENdR6cSM 7MrBh6t2Vac89bsa8COMs2CpU6sa6hdnJ0Zbueq7jvLx9Tzqg2PBKnZdYrhwyHutxkc1Kw2txUc7Nsvv3TPwkkU43YS ZMXxeLdOeZOG5zVW38/hmPZSX3nqu57HK 49mJ5F/R0N5ai/Oqvy1F/VrDDX0HuIn0X47hl4 SLUgVffX5Iu5mFonfq7Nc5baawwznOP3opbvbSf x5P/ae86/tZPHb 1N/zRzHncx55P4fm42cpvmMGnr4IGeoaeh188n5T8JyrPMd2augH90jP8a7OOcTd cDKdjg5LPyKyWEd8zw49kgDHnbiax/1q 6oRnHtg68anbby4mcZvnoGDhfhqw8Q/XnIfUHkWc3PKs8mz Y7M5BFeKL/XsVXFPY7P2xqsxgyA/szkEV4okWYwd0f3DyrPKtnzkAWYRbh6f4f9zMHPFpZmDszkEWYRZhFmBm4/AxkEeYluPxLsPPFEM5nf1lmEWYRZhFmBi4/A1mEeQku/xLkazv/Z2ft8swizCLMLMwOVnIIswL8HlX4KdL4ZwPvurMYswizCLMDNw RnIIsxLcPmXIF97n/21t/P7ZhFmEWYRZgYuPwNZhHkJLv8S7HwxhPPZX41ZhFmEWYSZgcvPwHIR/vXHn19c05 IhU9Y5Ve4YuqrXuX9UhxfOeRW1vt5XLVdzvPaF7/rCzZpdrqdzpRb6U41np80przX78bP1tvtG95nf9V95/cdF6EPq8fVtHJdXg90hMOdeF3ec0cxPbATv8sf5RyvHp47iqnZ4XEPbr3W8Z140pjyO5rhZPn8hBnYXoTdzdQLcvSSgHdcx4i111Guw6t yncYXCz9Kz7KOa61nU/O7dTLeRprjZ8DzPNVP2HOVZ5imvfzqL5i6rtWV0MPrVOeasDRGsfBPE9t7LUX9uEiZIB8UBgorOPEXq/8yae2rHLIa0598JXt OSw1BNPtnhg1GA1j18WH55qrDDlaw2 1qoPTv0uprzJ77RX3O4Mxfcaj7u6rrfyJg2voyY2i7D9N75uQHVYGDSsYuo7rvHke33x9HJc4yNfexZ3FYNNtqunPzVwPIYHrrbDNNdxd/S7OtVFAwumsfqut8LQurfGNR/RcQ2PVTP NRfi4Rchg6HDs/ILm/DSmjDN09P5msef6sDdOr9iv6iBO9nigVGD1bz6XqOY p0OOdfwuHT88lrw3Tw8P6PG6vuZqPf8UU2HV44L3Y6nGHwsWOw1F5//7g8vQgYK68LEheOX1XjyJ77m8VWDXNndvPM0xp/sbh/qOZ/G5fsFb1ffeaqvWp2v3Hv9o76qp701r77rebzi3oPpWeJnEdYMPLQIdXh8ABUrv3Dl7PiqoXzNq 8cjyfuxCOPrfodnz7K9dounuru4WpP9V1jF1Pe5HfaK253n8p3PY VW77Hqj9hrklN7LUX4rgIGRgfOB8YHTjH0MA6V Opj3I6fXLU7/DhYNHAksdWfuUXphc6ao9w79HFqgc 6U55r1PNqulitMCId/nUYbVO/cJ3YjhY1SWHdczz4LFZhP8b/isMxE95GX7KOZmZM533TGfh cSed9kuvwg/ Yc7 4ty9vN1s/E7z1y99erOl9x5F9Hv/m1 AT4AdSo3Sr6oAAAAAElFTkSuQmCC[/IMG]
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMoAAAAuCAYAAABpsIY8AAAF UlEQVR4Ae2aXXIcNwyE9zo Tw6Tkzt5lAup lytFkBilNWK68XDFH660SApYsZJ7e3ff36 zTNnMHdgfQduc0DrA5rzmfOJOzCDMl/U RdF4w7MoDQOab4q81WZQZlBmS9K4w7MoDQOab4o80WZQZlBmS9K4w7MoDQOab4o80X5PSi32 2tev7732O320PfPLGW0y7oiWu69xnpHtVf9VnxVthK8zTs96DowrLNZTmtGf/Pe t2/ Yr3gp7pjtzeVBi49nmyTtGjI3Dqbh6cMrv1qx46NFbe63qlIcGfKznNaaevisMPWqIqdW8 3BUX320qMv4GQc GHWeVzzDyFG/Whvck ylQdHNVX5szjGP9QAUq/LO8Zg6z2scvsedOjhhvX4XU6u8TEd5ylXf66jJ8tRh4RJjPe9aylM/4yne8V2DtZxqLw2KbqI6DD8A5TmWxfTQOvXBM s8jdX3vitM yhPfdfL4s/o7Hqopvpah49VHr5ilQ8Xu JVmOZDx2O0T7R3G5TYtD5s1g9DOfhw1a7qlKd VgO w1gLljq1qqF cDox2spV33WUj6/rUR8cCxax6xLDhUPeazXe1aw0tBYf7dPt3Qal2qj EfwQq5odzzXR8bzG6ru Y i5VZ76rufxinsF8/UQdzSUo/5qrcpTf1WzwlyD9T D/ZJB0QNR3w8xizk0rVO/W O8lcYKYz1X9Fbc6KX93Pe46l/lXd/X4rHzq/6e38Wsz3nkfR2aP9G/y6Cw6TgUPRjyvnF4zlWeY50a sHd6Tme1TmHOFsfWNgMJ4eFHzE5rGOeB8fuNOBhK772UT/qdjWKax981ci0lXeanw7KaYt8pfX4BXqlvZ 81xmUb/4JC29h7MmX5ZXXNoPyzYPyypfvmfY gzKDctxv6k4coBmUGZQZlMYdmEFpHNKJb7hZ02N/hDqDMoMyX5TGHZhBaRzSvL0f /Y 8bxnUGZQ5ovSuAMzKI1DOvENN2t67FduBmUGZb4ojTswg9I4pHl7P/btfeJ5z6DMoMwXpXEHZlAah3TiG27W9Niv3AzKDMp8URp34MOg/P3jrzee6q0VeIVFfoUrpr7qRd4fxfGVQ25lvZ/HUZvlPK998bO YJVmppvpVLmVblXj Uqjynt9N763XrfvvXjvBsU343E0jVyW1wXtcLgVL8t7bhfTA1vxs/wu53j08NwupqbDYw9uvdbxTlxpVPmO5p/IWQ5KtuE4wN0hgmdcx4i11y6X4VFf5TMMLpb Ee9yjmtt5pNzW/VynsZa4 sA83zUV5hzlaeY5n09qq Y q6V1dBD65SnGnC0xnEwz1N7xaaDQgMXoiHWcWKvV37lUxtWOeQ1pz74ymZ8cljqiSsbPDBqsJrHD4sPTzVWmPK1Bl9r1Qenvospr/Iz7RU3W0PwvcbjrC7rrbxKw uouWI/DEqnmXKyZo5rXPmqExx/HNd452vP4K5isMpm9fSnBo7H8MDVZpjmMm5HP6tTXTSwYBqr73orDK2rNa75GR3X8Fg1O/6HQdEiFV/5gVV46FWY5qu msev6sDdOj9if6iBW9nggVGD1bz6XqOY pkOOdfwOHT88Vrwbh6er1Fj9X1N1Ht V5PhkeNBN MpBh8L9hl7aVBoiK0aBq6YxpVf8TWPrxrkwnbzztMYv7LdPtSzPo3D9wdeV995qq9ama/cq/6ur ppb82r73oer7hXMF3LZ/z2oKi4L1Cx8ANXTsdXDeVrXn3neFxxKx55bNR3fPoo12uzuKq7wtWe6rtGF1Ne5WfaK262T W7nsfKDd9j1a8w16Tmin03KAj6glxQF QYGljnalz1UU6mT476Dh8OFg0seWzkV35g qCjdod7jyxWPfBKt8p7nWpGTRajBUbc5VOH1Tr1A /EcLCqSw7rmOfBr9gPg3Kl Jm49zisR z3WdbJWZy03q9cy8sMSvxhv/IguTj/x56 vmxv37nm6K1Ptr575V5qUO51aKPz2B8knnDeMyiNH8Sd8IeaNXzvcM6gzKC8 4/5Gch8IH8B/LQUfL qrFIAAAAASUVORK5CYII=[/IMG]
and I had overlooked the fact that there are further links below that one. Then bearing in mind your advice I just took a look at [http://old-releases.ubuntu.com/releases/18.04.4/](http://old-releases.ubuntu.com/releases/18.04.4/) once again and I looked for the string "18.04.4" at there and then I found the one displayed in attachment as "link of 18.04.4.png"
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAnwAAAAXCAYAAACRQZLmAAAJIUlEQVR4Ae2cXW4kOQ6EfZ197qPsYfYsfdCZefQiMPiAmBhSUlZW2 0yDSRIBoMhpYrOJKp/3v7684/3k vHjx/vun7 /PnQpdq3t7ejtU72M5yzz23Oac5pemB6YHpgemB6YHrg7WoTaGi7c11db/jTpNMD0wPTA9MD0wPTA9MD93rg8sA3B37vwOf85vymB6YHpgemB6YHpgc ugdm4Dv8I 2P/mBmvXkYTA9MD0wPTA9MD0wPPKsHjgc /g7fFfusTY7ONPz0wPTA9MD0wPTA9MD0wOM9cGngez/80VCoH9nv8uG8v7 9v9r1XT67uc/HHyBzdnN20wPTA9MDX6MHfunA952Gvlcb9nQ/80v8NX6J53Oaz2l6YHpgemB6YNcDDw98/Pcs1b/Y5Rs vhD8Dt/0zcA3v2y7X7bJT49MD0wPTA9MD3xWDzw08GnYqwY9sBz47n7T97///Pe3/7apGvh0HhUujLNacbL2as0VbdbymqtN ezP6dl6V /nM/nVvQvjOtlbpeF1u7xzx5 X1PRA3wP bJZfnZVzqrww59zRqfRdu8qfrl/VXtWuNFZYdxa555VGl u0T 6p0wR3jW4duFivAaus8461K6EK8yFuN/BpcfErW2nvsI94Md1dg4EJy4dB7Fa5Vew5/Ks1q/XRTJs1u88l83fP8Kres9fL9T8zznvbxblX8bMmORP3L/A5mzmb0x7Qc9O5GSuXWMbP5Phe8HO9jE/XR89tamV8R5vaSpPcai eq3zpVtqJZVxpJZY1GSdfcXIypqbCKww 9qFv CTslwZA/ZwMgix8xX7Ei vuGj486WwUY6ucYx0XTqWzqoGPRWdl4WLFvfIZiXv3DHO9nd4un3pfKfZ7c9/vYYd3edcYfwab6YHHe0DPy r8HHffuY67f4fjtfi/o3a3J/aMhYcFl62wFe61zkudjKnrcPJuO26H 35cp8If0UDzKQMff1dPVpvxS0MgV7fR6sXkGL4sFzeAhUMs6xg 9cTwEvc8mhVGjmFK91j5K0w5r4OL7XIV7pj7aFXWee5zb509PTN4lQ45rHOEeYwP1y052Q4nh4XntTufGqzzhXXa8OF4XVXjPPezLmPnup881kxcNX5lnjo4VX6wxweIObvXODs9R/ks3QeT7fCO0/E7HJ0u3 HUneyx0 hwtHf5XLviV9hJ3Y5zost9XLWddu7Jdb3Gfeec g8NfD7guV99w8ewR67aWPVicqx6uXhemhknttPI oxTL 9jN0h5Xh/aKvac/OSTr3DH3Kemss5zP /R4zyf3flW55caybmbTz3i1M1YvOqqeI7J9/h0vV0NefSJd3tc8diba1T8xHax641f99Gcy ufi56jfM7ug8l2eMfp B2OTpfvcOpO9thpdDiaq7yvj9/xE8 Y rTOc1 8jKntcPIndqXR5Rx3/2S95Dxl4GOY02byYiCEkxtQnC RxKr8Ccfr3GcPjrmf2hUfDLsbpDLv55S5jMVNTHHiu/iqBveWNs KvOPuk5d13H3n4Gf alzppEbFAXN7UldxdliV17qOy/c48 zzhAO30sh651Z88rs6eGNff9CZz/jfA4Oey9W5dDjczGfc8cCxz65DV/aKtrhcrnHid uwhyu6qbWL2V/ywE/trr7LO 7 6brOuz3wMchpI3kpxw88Xxy/emE45j41so67D8cx90/yOz4a2JNhCo7OCV82Y8 t8l7nPvUVRq7T9RruLW11NuI47r7XO 6 c/A9736VF1ZxEj/hoL y0uGCV2nvsCr/yJ4rnQpjr7lGFTt3ld tkzoTz D3yj2gZ6jfX8bkOrzLd/wO73R2 GlevG7tDr iDffKOo smzUZs48OJ7 zu/ou77j7rCcsL3Jpbw98uRCxD3sa mbg 3vI0/n40IXf4d1g5nhX2 Fey/pYr8lmIe5e8I7L7y50ZJOTOed4DtwxX7/DTzhe677vFdz13K/yFVbViOe4 2g4Z5f3GverOmF 7fi D eOP0Pdd wBPT/zvitMnA7vch2/w9lHl /wbn303HYaHX5S6xz8Sq/CxL LX61njyvbaXpNx3Hcfa91f8V5 sCXg94rfsPnL0RemgxMbnXwHsuvsBW yqElu7pyD2juaqr7VGNxz95kiXecrMnY61gfjudyvSqu6lIjOayJzTwx1vXcr/IVVtWI57j7aDhH dXlNe53uh2n43e464w/A Cr94Cep9U9fhSez3P28oz1n6XNnmS7fTkHv JW2Eo37yHj1VorXeo62 0z R3PcfeznnjFefrAx4CXdr7h 3Xf8FUDHUNdl twNQs5Giht94J33H2v73A4nndf avxiWbFAXOba5Nz3P0qX2FVjXiOu49GchzH7 pO87lGp9fhrDN2hr1X74HlS/bCIPgsHT/vTrPCK8y10u/4jrvv9R3uHPyKW2HidzhaaZOfMfwOJ1/ZKzUdN/GMfd1VTrzbA18Odl18ZeDTC8RfIhlr457vYue4zwE55v6JHhpYhiS3OnyP8RPPGJ7b5GTsXPwTDlys13Bvla3Oq8K8dpcX1znuo OY 1U 9YizLmO03FYcYY67T 0JlhzFFYambOY9h7/jZD7jap3kZMzaY2fI y49oGfm7l6Tk7HqKyx1k5Nx8omTl/Hp ui5Ta0qrjDX2PlZDz/xjOGtbFWTWMYrPXLPqOk0KrzC2Av29sCnRfx6ZODTZvTi4CJmk7xUyBOTx2beee47333qO6zSgMvA5Fbn4rH7/zyzf/Oq2l2N68vvNJLnsddwb53lvDgXrPOT4zn5ns/6jKkF91pyqek4OSz1yeli Fh04AvHx17BOl3Xcg54Z3drd3nWqPJaa5fv9jP4DIGv1gP TE4/79Xzq5zz5K 4mVvFrps8z6Wf3Cr2miov7ISzql3l0E6O8MQy7jhodvnU8dhr00 ex/KdnzmPnSffc53/2wx83Qa/Cu5D06v4X Xsr yzG2KuaAx3BpfpgemB6YHpga/WAzPwNf/J7tUP8lWGPL Pq2fwFfgz8M1D iv06exx nR6YHrg2T1we Dr/gg38dXf4Xv2TX2Gng9Kr J/xjn 6jVn4JuH6K/usdGfHpsemB74HXvg/5UnqKOlinM2AAAAAElFTkSuQmCC[/IMG]

I will try to install this one. I bet this one will install exactly the minor release I was looking for, 18.04.4.

Thanks for the advice about installing only packages of security patches. Anyway, I might also end up deciding to disable all updates, regardless of whether they have to do with security or not just to make sure I do not install something I should not.

Thanks a lot again.

---


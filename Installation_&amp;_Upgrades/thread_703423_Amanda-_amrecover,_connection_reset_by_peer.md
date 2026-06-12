---
title: "Amanda- amrecover, connection reset by peer"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by perund on 2008-02-21
I have a amanda server in subnet a.b.15.x and some clients on the same subnet and some in a.b.16.x. amdump works fine and amrecover on the clients on the same subnet. But the clients on the other subnets fails.

client log:
amrecover: connected to 10.10.15.22.10080
amrecover: our side is 0.0.0.0.516
amrecover: try_socksize: send buffer size is 65536
amrecover: try_socksize: receive buffer size is 65536
security_stream_seterr(0x805dcb0, recv error: Connection reset by peer)
security_seterror(handle=0x805cff8, driver=0xb7f75140 (BSDTCP) error=recv error: Connection reset by peer)
security_close(handle=0x805cff8, driver=0xb7f75140 (BSDTCP))
security_stream_close(0x805dcb0)

any ideas?

---


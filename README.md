# VPN-Blacklist
VPNを弾くためのASNリスト

Usage:
```js
export default {
  async fetch(request, env, ctx) {
    const cf = request.cf;
// ブロックしたいASNリスト
    const blockedAsns = []
    if (cf && cf.asn) {
      if (blockedAsns.includes(cf.asn)) {
        return new Response(`アクセス拒否: ASN ${cf.asn}`, {
          status: 403,
          headers: { "content-type": "text/plain;charset=UTF-8" },
        });
      }
    }
    return new Response(`アクセス許可: ASN ${cf?.asn || "不明"}`);
  },
};
```

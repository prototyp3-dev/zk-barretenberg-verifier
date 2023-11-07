# ZK Barretenberg Verifier

This is an example that uses [noir lang](https://noir-lang.org/) backend to verify the input in a Cartesi Rollups DApp.

DISCLAIMERS

This is not a final product and should not be used as one.

## Requirements

- [npm](https://docs.npmjs.com/cli/v9/configuring-npm/install) (To run sunodo)
- [Sunodo](https://github.com/sunodo/sunodo) (To build and run the DApp backend)

To install sunodo run:

```shell
npm install -g @sunodo/cli
```

## Interacting with the DApp

The DApp accepts json object, whose keys are the hex enconded public inputs and the proof. E.g.:

```json
{
  "proof": "0x0d8f...cf22",
  "merkle_root": "0x0958...8f3f",
  "nullifier_hash": "0x1797...1384"
}
```

To send advance requests you can use sunodo cli

```shell
sunodo send generic --chain-id=31337 --rpc-url=http://127.0.0.1:8545 \
    --mnemonic-index=1 --mnemonic-passphrase='test test test test test test test test test test test junk'\
    --dapp=0x70ac08179605AF2D9e75782b8DEcDD3c22aA4D0C --input=$proof_json
```

You can also send inspects

```shell
curl http://localhost:8080/inspect/$(echo $proof_json | jq -sRr @uri)
```

Hint: the following proof should generate a correct verification. You can use in the above tests. Change any bit to fail the verification.

```shell
proof_json='{"proof":"0d8f056208accdbd00201bc589cd5bb340c504bee52c94e68e7a52f3c32264d21af17c3ac7ab3e1f6c77c4ccd4857e5b7ad4071b8e016b53d14d4d05a0257db82fe02fd543931dadd465b3b572cc93630e5e163c83278fb39af1b425bcad85090e4fe86f1bb25fd4d244ee836d69c5f87d22d4e0e12c907ab11484a0a82d35ac2c24d84c09a0d83ed413fd4f0c9520789af7b68c6fb97aa3a4a9b5550a3a77081b0ef7ced44ff2916a20e437217078b35005fd0e2b124f359468ecf675868b8d198d401b59fa8419b78602fb82932f08aeaf7a367e85f7547bc93bd77837522203c8987b199809ab16cc1df3d11b4e9cba2019b79f19992878c2160758a2f7ea252a87ddba4d4949a90ecffed12c53932980dd99e8b7b3e190f42594cba1bdd421fea06c66790456ad30e304907d902cb337975c8ce08d7092340caa5958c89519efb083122bbf0876e305b33b66623adebd027f8931d70516bda75ee5cf5a2c15dbea153bbfcd740604dbaef189da31ee9cebadad289f5c6e9131ee56b6de6d1aa860ca8b13fac089de15182619007684bec6aa0478df3c07798a7c093807b023015d9501c43b1d68952a6b3e539c5bb3dafead3a8c15abb030e12e69f5f3162ce0580d421336b2eebd3075962e705937984c2e0e0ca893b8772c4c8032c5e61db7b69048f2ce72c625fe967cb36f31ef198bd6f53ad1ca8aedb948412596dc2e477a7950b2a1159289879b80de097e60417a2ede36f92710ea248c9768224f215d7f9c38668bb82a1b6a14d602dfd8078094bca84c16e3d92959fff9d3c60305ab3cc6462b1a34093419dded1d80dc51d72b6ea6db0e1dcadf512c42c8fdc3223095097c0e705901b4fe91c4afcc8ee05529df14782c9f82128743bb54574511971c7d748233a1d9aa73ddcdb3db399dfb5a879aad2a45a51efab8eb44a15929a21c4bfc276fb66a15ef65e351e49d88c506ff4849af22cdf1e6b23aba47b01f3864b675a4d9a38871cc6e734ce34fdea6df24b78a5bba069eb2c738ab0bf7034dabb1cd7a28eb1121b6860b83eced3cade811e3ab0a3a02cb3a1821995f86215bd9e0c5a4cfcd1ce595110e515a280ee275c924b25ca0c8f0adff9feb491925d99908a7db65211670bbe02a335245fc8bacd8dbeee2e3eb67b583942b2f300e73bc7d14aeb77cb18bc19cb4ad054f1a5d747e021ca08a705c508e22f7641f2e4d5decf5dbb28c2f75d790c6f919eec71baf7cf033f1146f9dc754ee18e70e0941ae95579cab9ebc0112bf2942b28c13e555ebb9f7326785f580a722f858d01a1827bc2f5efd41b2a0a952c25beecd7195f95854d9ac627a79ac8479f7e3c22b8a864dd214c7e1420670d3ebabe0a35ec27f97c5543a1e62118b8de073ee501c5c1f02daeedd21912a40fdf28ea474655de70a875f4fba50489b92e668333927ffec64ad558f318449fd997bb1a6cf92e928c06b48ea6cd6ab48088889dc1117f5022c1da0fc93178cebcdb0265dd649519d810f9a3b26289c6b1bd397aa022e9fe045c638105bfd0849f825b8fe003ede67fd9957f3d4504a4a91d785e8fc048ee576e848dcf2efad3ebedc030c101cc786e8d0b0b532b2496a8dc28123220f5e88f4c178f438a30a845c44926b0d9f097a473f384dccb3966b2fa8e85af216a8d91b07d4ac07a6d10d107450636309764d0da1413e19b571ec04709779070cf3f3c590b04d280261de6fbee9ad8adf2801c9a18defe25c1192efac19536500a6ed6a0a68064e210facfe9e9a128185fa3da3df96e677893c0427cee438d11ac8895b7e2efb90072d159bc739af0e6e7fd5165c674f993c633704bf13a11421c34e1292701432a9b59ba1359f33d942f7b59a72d5f6eb3f63c1d3ff45310a26bc266bf0ac7142b3e51f8eed6704d385efa2552e671fe617314dcc06c769c91207543d01feb18addab078a84c065cf0d7387069460e183a40812223b995d652eb0b029ac04b6e0aa4249bfb8d916f69ef2ff1fb4912a1a34708aa2795cfa6409a4f5ff3ffec0aaff2e4a8e5d51b13b7c4b54338586f5e5cece1d948bb5b48e1c018bd6e449675d6a6e6e2afdefafdc2fddbfd0a327039681a56cbb2f2f754f29204381a6d38ef919c69e2f41caf4933fdafb034308eec1a15de5b0264f034627bcadb8e23de0951fac23fe0623c0dd75a9a02d00dde6f632af178bfce4b807301805f661a821e06ee2e29fa346b62edfa3ec284db2edcb1a49943f413582742fbf8821a349e7e0af0438e708544eb9f12670312dfccd418600c374edc1c45f229b6910e9c2ada83d011602870d1b7df3c604e5d7e6618029429577ddf0468102f881a38ce7553d2cb214c97f14d10c93f4b25d22fe24cf18a9893f62c9e0052a6a4e78f0b853fb027eb6e47ff0377f656be85e1d7b71db2b364ffba786b1fb1abd4313ccb5cbc63a8ff2ba5965d09b038b6ffb541f45f3d8cfb325d3f30bfc061351a1c0fc74907be52a30d35a0e3bb7e3a4642165f94b3138b288fe29aa761eccc51e3ad652fafe4b967a5634472b89fef27e6b992843cbef28b117fb61f30610a693913834e8483ea1e55a4f96e440454459cbebe8bb94e51e420ed23f9d23575a569e792cac2770247bb811558e78c65a82dc73c1e2e2f8a7a42dfef254147907ec437ac52a0a850ba4e8ac67c5a916d1f94df70458f2547f06d22be8d70a28b0a9ea6ba7b69c27e7c46a6f09b452ddf4ce06896e1316a51f0091bce8290bfd35763a03168c22e3573ca7f316dc57973a3c99b800a986cfab9016a0b7be2c2f8a4c496e3427dd435fdbc0eb5f29df3b1d975589f09a70441b9415db9d82285f4fb391bd5f9eba3e6167e1f127b9d49522008cfcdd16873e749408245ab11ee7feb75e14970c65e7a306d313e8d5533d4efc5c73d03456ad0559b2580ba716449e874afab815fae2bbfefbd1bb81cf1b7e4caf6c8263dfebba7bd39e1b300f57098cc3ecf7c5a169e8e651c0bb2f823ec3219c598e245c8e5236e379cf22","merkle_root":"0x095826d5ce82ab5ee4442590b73e272714bac8ab5b1d6439f185016802688f3f","nullifier_hash":"0x1797522b58f30682ab2aff07a919a34dcf584987c0f9a098c86becb689bd1384"}'
```
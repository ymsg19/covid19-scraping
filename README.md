# COVID19 Scraping Script for Okayama

## What 's this?

岡山県公式 HP や岡山県オープンデータカタログサイトで公開されている情報を取得し、JSON として出力するスクリプトです。

[岡山県 新型コロナウイルス感染症対策サイト (非公式)](https://okayama.stopcovid19.jp) で使用する形に整形し、出力します。

## Make data

```
$ composer install
$ php convert.php
```

## Reference data list

このスクリプトでは、以下のデータを参照し、JSON を出力しています。

| ファイル名               | データの詳細                       | データの参照元                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------ | ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| contacts.json            | 一般電話相談件数                   | [オープンデータカタログサイト](http://www.okayama-opendata.jp/opendata/ga130Action.action?resourceName=%E4%B8%80%E8%88%AC%E9%9B%BB%E8%A9%B1%E7%9B%B8%E8%AB%87%E4%BB%B6%E6%95%B0&keyTitle=d9c4776db7f09fff161953a2aaf03b80a9abad48&title=%E6%96%B0%E5%9E%8B%E3%82%B3%E3%83%AD%E3%83%8A%E3%82%A6%E3%82%A4%E3%83%AB%E3%82%B9%E6%84%9F%E6%9F%93%E7%97%87%E3%81%AB%E9%96%A2%E3%81%99%E3%82%8B%E3%83%87%E3%83%BC%E3%82%BF%EF%BC%88%E5%B2%A1%E5%B1%B1%E7%9C%8C%EF%BC%89&isParam=1&action=clickLnkResourceNameList&resourceId=165b2f56-d472-4b71-8c81-f97f898f1923&datasetId=e6b3c1d2-2f1f-4735-b36e-e45d36d94761&checkFieldFormat=CSV)                                                                                                        |
| querents.json            | 帰国者・接触者相談センター相談件数 | [オープンデータカタログサイト](http://www.okayama-opendata.jp/opendata/ga130Action.action?resourceName=%E5%B8%B0%E5%9B%BD%E8%80%85%E3%83%BB%E6%8E%A5%E8%A7%A6%E8%80%85%E7%9B%B8%E8%AB%87%E3%82%BB%E3%83%B3%E3%82%BF%E3%83%BC%E7%9B%B8%E8%AB%87%E4%BB%B6%E6%95%B0&keyTitle=d9c4776db7f09fff161953a2aaf03b80a9abad48&title=%E6%96%B0%E5%9E%8B%E3%82%B3%E3%83%AD%E3%83%8A%E3%82%A6%E3%82%A4%E3%83%AB%E3%82%B9%E6%84%9F%E6%9F%93%E7%97%87%E3%81%AB%E9%96%A2%E3%81%99%E3%82%8B%E3%83%87%E3%83%BC%E3%82%BF%EF%BC%88%E5%B2%A1%E5%B1%B1%E7%9C%8C%EF%BC%89&isParam=1&action=clickLnkResourceNameList&resourceId=f38ae73f-73c1-4f34-8174-1b188c77c713&datasetId=e6b3c1d2-2f1f-4735-b36e-e45d36d94761&checkFieldFormat=CSV)                       |
| inspections_summary.json | PCR 検査実施人数                   | [オープンデータカタログサイト](http://www.okayama-opendata.jp/opendata/ga130Action.action?resourceName=%EF%BC%B0%EF%BC%A3%EF%BC%B2%E6%A4%9C%E6%9F%BB%E5%AE%9F%E6%96%BD%E4%BA%BA%E6%95%B0&keyTitle=d9c4776db7f09fff161953a2aaf03b80a9abad48&title=%E6%96%B0%E5%9E%8B%E3%82%B3%E3%83%AD%E3%83%8A%E3%82%A6%E3%82%A4%E3%83%AB%E3%82%B9%E6%84%9F%E6%9F%93%E7%97%87%E3%81%AB%E9%96%A2%E3%81%99%E3%82%8B%E3%83%87%E3%83%BC%E3%82%BF%EF%BC%88%E5%B2%A1%E5%B1%B1%E7%9C%8C%EF%BC%89&isParam=1&action=clickLnkResourceNameList&resourceId=60ecd874-0f71-4d9f-9a8a-936fad9c99bc&datasetId=e6b3c1d2-2f1f-4735-b36e-e45d36d94761&checkFieldFormat=CSV)                                                                                               |
| patients.json            | 感染者数                           | [オープンデータカタログサイト](http://www.okayama-opendata.jp/opendata/ga130PreAction.action?resourceName=%E6%84%9F%E6%9F%93%E8%80%85%E6%95%B0&keyTitle=d9c4776db7f09fff161953a2aaf03b80a9abad48&title=%E6%96%B0%E5%9E%8B%E3%82%B3%E3%83%AD%E3%83%8A%E3%82%A6%E3%82%A4%E3%83%AB%E3%82%B9%E6%84%9F%E6%9F%93%E7%97%87%E3%81%AB%E9%96%A2%E3%81%99%E3%82%8B%E3%83%87%E3%83%BC%E3%82%BF%EF%BC%88%E5%B2%A1%E5%B1%B1%E7%9C%8C%EF%BC%89&isParam=1&resourceId=0c728c2e-a366-421d-95df-86b6b5ad15fd&licenseTitle=%E3%82%AF%E3%83%AA%E3%82%A8%E3%82%A4%E3%83%86%E3%82%A3%E3%83%96%E3%83%BB%E3%82%B3%E3%83%A2%E3%83%B3%E3%82%BA+%E8%A1%A8%E7%A4%BA&datasetId=e6b3c1d2-2f1f-4735-b36e-e45d36d94761&checkFieldFormat=CSV)                            |
| patients_summary.json    | 感染者詳細情報                     | [オープンデータカタログサイト](http://www.okayama-opendata.jp/opendata/ga130PreAction.action?resourceName=%E6%84%9F%E6%9F%93%E8%80%85%E8%A9%B3%E7%B4%B0%E6%83%85%E5%A0%B1&keyTitle=d9c4776db7f09fff161953a2aaf03b80a9abad48&title=%E6%96%B0%E5%9E%8B%E3%82%B3%E3%83%AD%E3%83%8A%E3%82%A6%E3%82%A4%E3%83%AB%E3%82%B9%E6%84%9F%E6%9F%93%E7%97%87%E3%81%AB%E9%96%A2%E3%81%99%E3%82%8B%E3%83%87%E3%83%BC%E3%82%BF%EF%BC%88%E5%B2%A1%E5%B1%B1%E7%9C%8C%EF%BC%89&isParam=1&resourceId=c6503ebc-b2e9-414c-aae7-7374f4801e21&licenseTitle=%E3%82%AF%E3%83%AA%E3%82%A8%E3%82%A4%E3%83%86%E3%82%A3%E3%83%96%E3%83%BB%E3%82%B3%E3%83%A2%E3%83%B3%E3%82%BA+%E8%A1%A8%E7%A4%BA&datasetId=e6b3c1d2-2f1f-4735-b36e-e45d36d94761&checkFieldFormat=CSV) |

## LICENSE

このスクリプトは、[MIT ライセンス](https://github.com/stopcovid19-okayama/covid19-scraping/blob/master/LICENSE)で公開されています。

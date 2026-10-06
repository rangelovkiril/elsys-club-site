# elsys.club - общата страница на клубовете

Сорсът на страницата на [elsys.club](https://elsys.club/) - каталогът на клубовете в ТУЕС и информацията за панаира.

Страницата е статична: `index.html`, `style.css` и логата в `assets/`. Няма framework, няма build step - това, което е в `main`, е това, което се сервира.

## Кредит

Първата версия на страницата е направена от [@DebelToni](https://github.com/DebelToni) (Антон Христов) - вижте първия commit в историята. Пренесена е тук от [rangelovkiril/elsys-club-dns#9](https://github.com/rangelovkiril/elsys-club-dns/pull/9), където беше предложена като един self-contained файл от 275 KB; оттогава CSS-ът и логата са изнесени в отделни файлове, а съдържанието се допълва с PR-ове.

## Хостинг

Деплойва се автоматично на **Cloudflare Pages** (проект `elsys-club-site`) при всеки push в `main`. Всеки PR получава свой preview URL - там се проверява промяната, преди да влезе.

- production: <https://elsys.club/> (и `www.elsys.club`, същото съдържание)
- Pages поддомейн: <https://elsys-club-site.pages.dev/>

## Съдържание тук, DNS там

Правилото е просто:

| Какво | Къде |
|---|---|
| HTML, CSS, лога, текстове на клубовете | **това репо** |
| DNS записи за `elsys.club` и поддомейните на клубовете | [rangelovkiril/elsys-club-dns](https://github.com/rangelovkiril/elsys-club-dns) |

DNS репото управлява само записи и не хоства нищо - вижте „Обхват на репото“ в неговото README. Решението страницата да живее тук, а не там, е по [elsys-club-dns#10](https://github.com/rangelovkiril/elsys-club-dns/issues/10).

Записите `elsys.club` (apex) и `www.elsys.club` сочат към Pages проекта и са описани в `root.yaml` на DNS репото. Името на проекта е част от DNS записа - **не преименувайте Pages проекта** без PR там.

## Как се добавя или променя клуб

1. Branch и PR към `main`. Един PR - един клуб, по възможност.
2. Лого: сложете файла в `assets/` с **малки букви** в името (Cloudflare Pages е case-sensitive - `assets/Logo.png`, реферирано като `assets/logo.png`, работи локално и 404-ва в production). Квадратно изображение е най-добре: CSS-ът фиксира `136x136 px` с `object-fit: contain`.
3. Клуб без своя страница оставя бутона `<button class="club-link" disabled>Няма страница</button>`. Клуб със страница я заявява като поддомейн в DNS репото и слага `<a class="club-link" href="…">`.
4. Отворете preview URL-а от PR-а и проверете на тясно (375 px) и широко.

## Лиценз

MIT - вижте [LICENSE](LICENSE). Кодът е MIT; логата са собственост на съответните клубове и са тук с тяхно съгласие.

---
layout: single
title: "1학기 마무리(미완)"
---
⊙ 요구사항
주사위 5개를 굴림
원하는 주사위를 고르고 나머지는 다시 돌림
한라운드에 최대 두번(주사위 굴리는 횟수는 총 3번)
반드시 점수판에 점수 기록
총 13라운드

-기록법-
ace 1이나온 주사위 합
two 2가 나온 주사위 합
three 3이 나온 주사위의 합
fours 4가 나온 주사위 합
five 5가 나온 주사위 합
Three-Of-A-Kind 주사위 3개 이상의 눈이 동일할 때, 주사위 5개의 합
Four-Of-A-Kind
주사위 4개 이상의 눈이 동일할 때, 주사위 5개의 합
Full House
눈이 동일한 주사위가 각각 3개와 2개가 있을 때, 고정 25점
Small Straight
주사위 4개 이상의 눈이 이어지는 수일 때, 고정 30점
Large Straight
주사위 5개의 눈이 이어지는 수일 때, 고정 40점
Chance
주사위 5개의 눈의 총합
Yahtzee
주사위 5개의 눈이 모두 같을 때, 고정 50점
Yahtzee 보너스
야찌가 또 나올경우, 100점 추가

~~~python
import random
realscoreace = 0
realscoretwo = 0
realscorethree= 0
realscorefour= 0
realscorefive= 0
realscoresix = 0
realscoretok= 0
realscorefok = 0
realscorefh= 0
realscorels= 0
realscoress= 0
realscoreyacht= 0
realscoreyachtbonus= 0
realscorechance= 0
def scorerules():
  scoreretry = 1
  while scoreretry != 0:
    z = input('어디에 점수를 입력할까요?:')
    if z == 'ace':
      preventlapace = 1
      if preventlapace <= 0:
        continue
      else :
        acelst = [dice1,dice2,dice3,dice4,dice5]
        score = acelst.count(1)
        preventlapace -= 1
        scoreretry -= 1
        realscoreace = score
    elif z == 'two':
      prventlaptwo = 1
      if preventlaptwo <= 0:
        continue
      else :
        preventlaptwo = 1
        twolst =[dice1,dice2,dice3,dice4,dice5]
        score = twolst.count(2)*2
        preventlaptwo -= 1
        scoreretry -= 1
        realscoretwo = score
    elif z == 'three':
      prevetlapthree = 1
      if preventlapthree <= 0:
        continue
      else :
        threelst = [dice1,dice2,dice3,dice4,dice5]
        score = threelst.count(3)*3
        preventlapthree -= 1
        scoreretry -= 1
        realscorethree = score
    elif z == 'four':
      preventlapfour = 1
      if preventlapfour <= 0:
        continue
      else :
        fourlst = [dice1,dice2,dice3,dice4,dice5]
        score = fourlst.count(4)*4
        preventlapfour -= 1
        scoreretry -= 1
        realscorefour = score
    elif z == 'five':
      preventlapfive = 1
      if preventlapfive <= 0:
        continue
      else :
        fivelst = [dice1,dice2,dice3,dice4,dice5]
        score = fivelst.count(5)*5
        preventlapfive -= 1
        scoreretry -= 1
        realscorefive = score
    elif z == 'six':
      preventlapsix = 1
      if preventlapsix <= 0:
        continue
      else :
        fivelst = [dice1,dice2,dice3,dice4,dice5]
        score = fivelst.count(6)*6
        preventlapsix -= 1
        scoreretry -= 1
        realscoresix = score

    elif z == 'chance':
      preventlapchance = 1
      if preventlapchance <= 0:
        continue
      else:
        chacelst = [dice1,dice2,dice3,dice4,dice5]
        score = dice1 + dice2 + dice3 + dice4 + dice5
        preventlapchance -= 1
        scoreretry -= 1
        realscorechance = score
    elif z == 'fok':
      preventlapfok = 1
      if preventlapfok <= 0:
        continue
      else:
        foklst = [dice1,dice2,dice3,dice4,dice5]
        numfok = 0
        preventlapfok -=1
        for k in range(6):
          numfok += 1
          if foklst.count(numfok) >= 4:
            score = dice1 + dice2 + dice3 + dice4 + dice5
            break
          elif foklst.count(numfok) < 4:
            continue
        realscorefok = score
        scoreretry -= 1
    elif z == 'tok':
      preventlaptok = 1
      if preventlaptok == 0:
        continue
      else :
        toklst = [dice1,dice2,dice3,dice4,dice5]
        preventlaptok -= 1
        numtok = 0
        for k in range(6):
          numtok += 1
          if toklst.count(numtok) >= 4:
            score = dice1 + dice2 + dice3 + dice4 + dice5
            break
          elif foklst.count(numtok) < 4:
            continue
        realscoretok= score
        scoreretry -= 1
    elif z == 'fh':
      preventlapfh = 1
      if preventlapfh == 0:
        continue
      else:
        fhlst = [dice1,dice2,dice3,dice4,dice5]
        fhnum = 0
        fhnum1 = 0
        preventlapfh -= 1
        score = 0
        for t in range(6):
          fhnum += 1
          fhnum1 += 1
          if fhlst.count(fhnum) == 3:
            if fhlst.count(fhnum1) == 2:
              score = 25
              break
        realscorefh= score
        scoreretry -= 1
    elif z == 'yacht':
      preventlapyacht = 1
      if preventlapyacht == 0:
        continue
      yalst = [dice1,dice2,dice3,dice4,dice5]
      yanum = 0
      yanum1 = 0
      score = 0
      yachtlap = 0
      for ya in range(6):
        yanum  += 1
        if yalst.count(yanum) == 5:
          score = 50
          yachtlap += 1
          realscoreyacht= score
          if yachtlap == 1:
            print('야추 보너스!')
            score = 100
            realscoreyachtbonus = score
            yachtlap += 1
          elif yachtlap > 1:
            print('운이 좋네;;하지만 다시')
            preventlapyacht -= 1
      scoreretry -= 1
    elif z == 'ss':
      preventlapss = 1
      if preventlapss == 0:
        continue
      else:
        preventlapss -= 1
        sslst = [dice1,dice2,dice3,dice4,dice5]
        sslst.sort()
        ssnum = 0
        ssscore = 0
        score = 0
        for retry in range(4):
          if sslst[ssnum] + 1 == sslst[ssnum + 1]:
            ssscore += 1
          else :
            continue
        if ssscore >= 4:
          score = 30
        realscoress= score
        scoreretry -= 1
    elif z == 'ls':
      preventlapls = 1
      if preventlapls == 0:
        continue
      else:
        lslst = [dice1,dice2,dice3,dice4,dice5]
        lslst.sort()
        preventlapls -= 1
        lsscore = 0
        lsnum =0
        score = 0
        for retryls in range(4):
          if lslst[lsnum] + 1 == lslst[lsnum + 1]:
            lsscore += 1
          else :
            continue
        if lsscore == 5:
          score = 40
      scoreretry -= 1
      realscorels = score
  scoreretry = 1
    
for x in range(13):
  print('ace : {} || two : {} || three : {} || four : {} || five : {} || six : {} || tok : {} || fok : {} || fh : {} || ss : {} || ls : {} || chance : {} || yacht : {} || yachtbonus : {}'.format(realscoreace,realscoretwo,realscorethree,realscorefour,realscorefive,realscoresix,realscoretok,realscorefok,realscorefh,realscoress,realscorels,realscorechance,realscoreyacht,realscoreyachtbonus))
  dice1 = random.randrange(1,7)
  dice2 = random.randrange(1,7)
  dice3 = random.randrange(1,7)
  dice4 = random.randrange(1,7)
  dice5 = random.randrange(1,7)
  print(dice1,dice2,dice3,dice4,dice5)
  dicelist = [dice1,dice2,dice3,dice4,dice5]
  overlap = []
  i = 1
  for repeat in range(2):
    dre = input('주사위를 더 돌릴까요?:')
    if dre == 'y':
      dre3 = int(input('주사위를 몇개 돌려야 하나요?:'))
      while dre3 != 0:
        dre2 = int(input('몇번주사위를 돌릴까요?:'))
        overlap.append(dre2)
        dre2 -= 1
        if overlap.count(i) < 2:
          dicelist[dre2] = random.randrange(1,7)
          i += 1
          dre3 -= 1
        elif overlap >= 2:
          print('같은 주사위를 또 돌릴 수 없습니다.')
    elif dre == 'n':
      overlap.clear()
      break
  print(dice1,dice2,dice3,dice4,dice5)
  scorerules()

~~~



# AI-homework

## 연합학습
![image](https://user-images.githubusercontent.com/48613073/192774714-60dcfb52-406a-4d04-9b5d-16298793a011.png)

* 데이터를 개개인의 로컬 클라이언트에 두고 그 로컬 클라이언트에서 학습을 수행한 후, 업데이트된 모델의 파라미터들을 중앙 서버로 보내 취합해서 하나의 모델을 업데이트 하는 것
* 데이터가 아닌 학습을 통해 도출된 가중치들만 중앙 서버로 전송이 됨

  * 데이터 유출 위험이 줄고 커뮤니케이션 효율성이 올라감
 ### 연합학습이 처음 제안된 논문
 ### "Communication-Efficient Learning of Deep Networks from Decentralized Data (McMahan et al., 2016: https://arxiv.org/abs/1602.05629)"
  ![image](https://user-images.githubusercontent.com/48613073/192775185-8f677b29-af47-4442-abdd-eeaa565b42b1.png)

***
## Femnist 데이터를 이용하여 연합학습 진행
* Femnist 필기체 데이터(숫자, 소문자, 대문자)
* 데이터 개수: 637,877개
![image](https://user-images.githubusercontent.com/48613073/192770739-20e9a75a-570e-4e7a-8170-6d372ce8f429.png)


## 훈련 모델
![image](https://user-images.githubusercontent.com/48613073/192770583-1e1a263c-4197-457e-ab0e-b84dea0217e0.png)


## server.py
![image](https://user-images.githubusercontent.com/48613073/192772045-0b7522a7-60ff-4016-9f7e-7bc202c87409.png)

## client.py 실행
    INFO flower 2022-09-28 20:54:21,138 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
    INFO flower 2022-09-28 20:54:21,138 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
    DEBUG flower 2022-09-28 20:54:21,139 | connection.py:39 | ChannelConnectivity.IDLE
    DEBUG flower 2022-09-28 20:54:21,139 | connection.py:39 | ChannelConnectivity.IDLE
    DEBUG flower 2022-09-28 20:54:21,139 | connection.py:39 | ChannelConnectivity.CONNECTING
    DEBUG flower 2022-09-28 20:54:21,139 | connection.py:39 | ChannelConnectivity.READY
    DEBUG flower 2022-09-28 20:54:21,139 | connection.py:39 | ChannelConnectivity.READY
    INFO flower 2022-09-28 20:54:21,140 | connection.py:102 | Opened insecure gRPC connection (no certificates were passed)
    DEBUG flower 2022-09-28 20:54:21,141 | connection.py:39 | ChannelConnectivity.IDLE
    DEBUG flower 2022-09-28 20:54:21,141 | connection.py:39 | ChannelConnectivity.CONNECTING
    DEBUG flower 2022-09-28 20:54:21,142 | connection.py:39 | ChannelConnectivity.READY
    
    number : 30, subject number : 60
    number : 10, subject number : 57
    number : 22, subject number : 27
    number : 7, subject number : 83
    number : 9, subject number : 8
    number : 11, subject number : 84
    number : 32, subject number : 73
    number : 20, subject number : 65
    .
    .
    .
    number : 1, subject number : 75
    number : 22, subject number : 77
    number : 13, subject number : 22
    number : 28, subject number : 44
    number : 35, subject number : 53
    DEBUG flower 2022-09-28 21:17:46,238 | connection.py:121 | gRPC channel closed
    DEBUG flower 2022-09-28 21:17:46,238 | connection.py:121 | gRPC channel closed
    DEBUG flower 2022-09-28 21:17:46,238 | connection.py:121 | gRPC channel closed
    INFO flower 2022-09-28 21:17:46,238 | app.py:149 | Disconnect and shut down
    INFO flower 2022-09-28 21:17:46,238 | app.py:149 | Disconnect and shut down
    INFO flower 2022-09-28 21:17:46,239 | app.py:149 | Disconnect and shut down

## 실험 결과
    DEBUG flower 2022-09-28 21:17:19,419 | server.py:179 | evaluate_round 98 received 3 results and 0 failures
    DEBUG flower 2022-09-28 21:17:19,419 | server.py:215 | fit_round 99: strategy sampled 3 clients (out of 3)
    DEBUG flower 2022-09-28 21:17:28,221 | server.py:229 | fit_round 99 received 3 results and 0 failures
    DEBUG flower 2022-09-28 21:17:28,287 | server.py:165 | evaluate_round 99: strategy sampled 3 clients (out of 3)
    accuracy : 0.12307692307692308
    DEBUG flower 2022-09-28 21:17:32,395 | server.py:179 | evaluate_round 99 received 3 results and 0 failures
    DEBUG flower 2022-09-28 21:17:32,395 | server.py:215 | fit_round 100: strategy sampled 3 clients (out of 3)
    DEBUG flower 2022-09-28 21:17:42,476 | server.py:229 | fit_round 100 received 3 results and 0 failures
    DEBUG flower 2022-09-28 21:17:42,539 | server.py:165 | evaluate_round 100: strategy sampled 3 clients (out of 3)
    DEBUG flower 2022-09-28 21:17:46,222 | server.py:179 | evaluate_round 100 received 3 results and 0 failures
    INFO flower 2022-09-28 21:17:46,222 | server.py:144 | FL finished in 1404.9710544
    INFO flower 2022-09-28 21:17:46,226 | app.py:180 | app_fit: losses_distributed [(1, 4.110625732375915), (2, 4.106114783757169), (3, 4.09253091242776), (4, 4.056104669031107), (5, 4.041994401853379), (6, 4.014894354170647), (7, 4.009860932072507), (8, 3.980154894400334), (9, 3.971356377005577), (10, 3.872176424662272), (11, 3.686430799717806), (12, 3.8395260014111483), (13, 3.663191732993493), (14, 3.745093868838416), (15, 3.6538322241801136), (16, 3.688771186556135), (17, 3.682391228214387), (18, 3.549312162399292), (19, 3.624263399297541), (20, 3.8202092460557524), (21, 3.8336722924159123), (22, 3.7450866997241974), (23, 3.990278023260611), (24, 3.6737317132949827), (25, 3.7832413659968847), (26, 3.8441905610701617), (27, 3.4216296672821045), (28, 3.616208533982973), (29, 3.7184563726186752), (30, 3.6506775617599487), (31, 3.686576195767051), (32, 3.759843929314319), (33, 3.4826016814209693), (34, 3.732817918826372), (35, 3.7081189155578613), (36, 3.693321473562895), (37, 3.766996514169793), (38, 3.5234991578913446), (39, 3.862467578479222), (40, 3.5908730725447335), (41, 3.684640020132065), (42, 3.94094103845683), (43, 3.7365372557389107), (44, 3.5786981271660845), (45, 3.7461052562879478), (46, 3.5491243623337656), (47, 3.624867747101603), (48, 3.5502932548522947), (49, 3.802321859995524), (50, 3.5317525068918862), (51, 3.627661108970642), (52, 3.5357038415508506), (53, 3.740665656974517), (54, 3.7703980428201183), (55, 3.7992605048677195), (56, 3.680407991312971), (57, 3.507105531692505), (58, 3.6408568105579895), (59, 3.6929975946744285), (60, 3.790175261122457), (61, 3.395160061972482), (62, 3.7168404424891754), (63, 3.7647409296747463), (64, 3.553560997500564), (65, 3.7516508392385535), (66, 3.718060933626615), (67, 3.6716779482246626), (68, 3.8206151499606595), (69, 3.7915690561820723), (70, 3.616716429338617), (71, 3.788813711267657), (72, 3.3144972782868605), (73, 3.9317453686071904), (74, 3.604228890343998), (75, 3.8246748819947243), (76, 3.7603514259808684), (77, 3.7881812390528227), (78, 3.7137640208414155), (79, 3.4929463421856917), (80, 3.8396358195039415), (81, 3.6548740680401144), (82, 3.6077535277918766), (83, 3.6006802774610973), (84, 3.706688053905964), (85, 3.609395464261373), (86, 3.838450881018155), (87, 3.925176730281428), (88, 3.892739356832301), (89, 3.8306424295580066), (90, 3.7596537639845664), (91, 3.886397116620776), (92, 3.8356945974784984), (93, 3.5815292458201564), (94, 3.7119151798646843), (95, 4.005745728810628), (96, 3.69285889934091), (97, 3.938529126022173), (98, 3.61934933942907), (99, 3.544214941905095), (100, 3.3974640369415283)]
    INFO flower 2022-09-28 21:17:46,226 | app.py:181 | app_fit: metrics_distributed {'accuracy': [(1, 0.04819277108433735), (2, 0.04225352112676056), (3, 0.07462686567164178), (4, 0.07547169811320754), (5, 0.0), (6, 0.014492753623188406), (7, 0.0379746835443038), (8, 0.014492753623188406), (9, 0.046875), (10, 0.016666666666666666), (11, 0.02040816326530612), (12, 0.0379746835443038), (13, 0.015384615384615385), (14, 0.1111111111111111), (15, 0.0), (16, 0.07142857142857142), (17, 0.016129032258064516), (18, 0.03076923076923077), (19, 0.01818181818181818), (20, 0.0), (21, 0.015384615384615385), (22, 0.03125), (23, 0.04938271604938271), (24, 0.03), (25, 0.09859154929577464), (26, 0.011764705882352941), (27, 0.10869565217391304), (28, 0.04054054054054054), (29, 0.0625), (30, 0.0641025641025641), (31, 0.042105263157894736), (32, 0.012345679012345678), (33, 0.0), (34, 0.038461538461538464), (35, 0.08333333333333333), (36, 0.029850746268656716), (37, 0.06315789473684211), (38, 0.1044776119402985), (39, 0.047619047619047616), (40, 0.125), (41, 0.078125), (42, 0.06818181818181818), (43, 0.05263157894736842), (44, 0.043478260869565216), (45, 0.05434782608695652), (46, 0.05660377358490566), (47, 0.06329113924050633), (48, 0.08333333333333333), (49, 0.06666666666666667), (50, 0.16666666666666666), (51, 0.027777777777777776), (52, 0.07407407407407407), (53, 0.060240963855421686), (54, 0.07407407407407407), (55, 0.03260869565217391), (56, 0.030303030303030304), (57, 0.14), (58, 0.037037037037037035), (59, 0.027777777777777776), (60, 0.0449438202247191), (61, 0.047619047619047616), (62, 0.07352941176470588), (63, 0.07462686567164178), (64, 0.15151515151515152), (65, 0.05405405405405406), (66, 0.0), (67, 0.06930693069306931), (68, 0.039603960396039604), (69, 0.034482758620689655), (70, 0.06779661016949153), (71, 0.008849557522123894), (72, 0.17307692307692307), (73, 0.10204081632653061), (74, 0.033707865168539325), (75, 0.0), (76, 0.0547945205479452), (77, 0.02631578947368421), (78, 0.0821917808219178), (79, 0.037037037037037035), (80, 0.05154639175257732), (81, 0.10256410256410256), (82, 0.14035087719298245), (83, 0.11904761904761904), (84, 0.07291666666666667), (85, 0.037037037037037035), (86, 0.0), (87, 0.02631578947368421), (88, 0.02127659574468085), (89, 0.04054054054054054), (90, 0.11940298507462686), (91, 0.04225352112676056), (92, 0.05263157894736842), (93, 0.06976744186046512), (94, 0.05970149253731343), (95, 0.049019607843137254), (96, 0.04411764705882353), (97, 0.043478260869565216), (98, 0.08823529411764706), (99, 0.12307692307692308), (100, 0.16)]}
    accuracy : 0.16
    INFO flower 2022-09-28 21:17:46,233 | app.py:182 | app_fit: losses_centralized []
    INFO flower 2022-09-28 21:17:46,233 | app.py:183 | app_fit: metrics_centralized {}
